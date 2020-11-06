ifdef OUTPUT
override OUTPUT = -DOUTPUT
endif


# C compiler
CC = gcc
CC_FLAGS = -g -O3 -Wall -fopenmp -I$(MATRIX_DIR)

# Matrix library path
MATRIX_DIR = ../meschach_lib


leukocyte: detect_main.o avilib.o find_ellipse.o track_ellipse.o misc_math.o $(MATRIX_DIR)
        $(CC) $(CC_FLAGS) -lm avilib.o find_ellipse.o track_ellipse.o misc_math.o detect_main.o -o leukocyte -lm $(MATRIX_DIR)/meschach.a -lpthread

%.o: %.[ch]
        $(CC) $(OUTPUT) $(CC_FLAGS) $< -c

detect_main.o: find_ellipse.h track_ellipse.h avilib.h

find_ellipse.o:
        gcc -g -O3 -Wall find_ellipse.c -I../meschach_lib -c

track_ellipse.o:
        gcc -g -O3 -Wall track_ellipse.c -I../meschach_lib -c

misc_math.o:
        gcc -g -O3 -Wall misc_math.c -I../meschach_lib -c

avilib.o:
        gcc -g -O3 -Wall avilib.c -I../meschach_lib -c

$(MATRIX_DIR)/meschach.a:
        cd $(MATRIX_DIR); ./configure --with-all; make all; make clean

clean:
        rm -f *.o leukocyte
