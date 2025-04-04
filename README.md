# CBT419
Converted to GitHub via [cbt2git](https://github.com/wizardofzos/cbt2git)

This is still a work in progress. GitHub repos will be deleted and created during this period...

```
//***FILE 419 is from David Rivers of Dignus in North Carolina,     *   FILE 419
//*           and contains C language programs which were compiled  *   FILE 419
//*           with the Dignus C Compiler whose output is OS/390     *   FILE 419
//*           MVS assembler language.  Programs are presented       *   FILE 419
//*           with C language source code, and the assembler        *   FILE 419
//*           language program that results when the C source is    *   FILE 419
//*           compiled with the Dignus compiler.                    *   FILE 419
//*                                                                 *   FILE 419
//*              Dave Rivers                                        *   FILE 419
//*              Dignus, LLC                                        *   FILE 419
//*              8924 Windjammer Drive                              *   FILE 419
//*              Raleigh, NC     27615                              *   FILE 419
//*              phone:  (919) 676-0847                             *   FILE 419
//*              FAX:  (919) 676-0847                               *   FILE 419
//*              email:  rivers@dignus.com                          *   FILE 419
//*                                                                 *   FILE 419
//*           Executable modules for these programs are provided    *   FILE 419
//*           on File 420 of this tape.                             *   FILE 419
//*                                                                 *   FILE 419
//*           More information about the Dignus C Compiler can be   *   FILE 419
//*           found at:     http://www.dignus.com                   *   FILE 419
//*                                                                 *   FILE 419
//*           A full manual for these programs and all the          *   FILE 419
//*           executable programs in the load module library        *   FILE 419
//*           on File 420, can be found in member $DIGNUS on        *   FILE 419
//*           this file.                                            *   FILE 419
//*                                                                 *   FILE 419
//*           All copyright restrictions and stipulations           *   FILE 419
//*           about programs found in Files 419 and 420,            *   FILE 419
//*           are detailed in member $DIGNUS, under the             *   FILE 419
//*           instructions for each program.                        *   FILE 419
//*                                                                 *   FILE 419
//*     This PDS contains two programs that are typically           *   FILE 419
//*     available on UNIX systems,  the `what' program and          *   FILE 419
//*     the `grep' program.                                         *   FILE 419
//*                                                                 *   FILE 419
//*     You should find the following:                              *   FILE 419
//*                                                                 *   FILE 419
//*     grep@c   -    The C source code for a grep clone,           *   FILE 419
//*                   originally taken from the DECUS               *   FILE 419
//*                   tape.  Modified for running under             *   FILE 419
//*                   OS/390.                                       *   FILE 419
//*                                                                 *   FILE 419
//*     grep@a   -    The assembly source generated                 *   FILE 419
//*                   with the Systems/C compiler.                  *   FILE 419
//*                                                                 *   FILE 419
//*     what@c   -    The C source code for the 'what'              *   FILE 419
//*                   program, from the Berkeley                    *   FILE 419
//*                   distribution.  Modified for running           *   FILE 419
//*                   under OS/390                                  *   FILE 419
//*                                                                 *   FILE 419
//*     what@a   -    The assembly source generated                 *   FILE 419
//*                   with the Systems/C compiler.                  *   FILE 419
//*                                                                 *   FILE 419
//*     We have included the assembly source for these programs     *   FILE 419
//*     in case someone wants to "pull out" one of the routines     *   FILE 419
//*     (particularly, the regular expression routines in grep)     *   FILE 419
//*     for inclusion in other programs.  You should be able to     *   FILE 419
//*     extract the function, adjust the prologue/epilogue          *   FILE 419
//*     correctly and include these in your own programs.   The     *   FILE 419
//*     code is non-rent, and uses R12 as the base register and     *   FILE 419
//*     R13 as the frame base register.  You should replace         *   FILE 419
//*     DCCPRLG and DCCEPIL with the appropriate function           *   FILE 419
//*     entry/exit macros.  The FRAMESIZE parameter on DCCPRLG      *   FILE 419
//*     indicates how much dynamic storage the routine will         *   FILE 419
//*     need.                                                       *   FILE 419
//*                                                                 *   FILE 419
//*     However, you should be able to compile the C source with    *   FILE 419
//*     other C compiler implementations for the mainframe.         *   FILE 419
//*                                                                 *   FILE 419
//*     Also, if you want to download the executables, we have      *   FILE 419
//*     them on our web site - http://www.dignus.com - and on       *   FILE 419
//*     File 420 of this tape.                                      *   FILE 419
//*                                                                 *   FILE 419
//*     Just what are these?                                        *   FILE 419
//*                                                                 *   FILE 419
//*   GREP:                                                         *   FILE 419
//*       General Regular Expression Processor.                     *   FILE 419
//*                                                                 *   FILE 419
//*             Read a file, looking for lines that                 *   FILE 419
//*             match a specified pattern.                          *   FILE 419
//*                                                                 *   FILE 419
//*   WHAT:                                                         *   FILE 419
//*       Show what versions of object modules were used            *   FILE 419
//*       to construct a file                                       *   FILE 419
//*                                                                 *   FILE 419
//*             On some source management systems, it's             *   FILE 419
//*             possible to embed an ID string in the               *   FILE 419
//*             source which will then appear in the                *   FILE 419
//*             object deck or load module for a                    *   FILE 419
//*             program.   This ID usually contains the             *   FILE 419
//*             file name, revisision number, check-in              *   FILE 419
//*             date, etc...                                        *   FILE 419
//*                                                                 *   FILE 419
//*             Thus, using WHAT, you can scan an object            *   FILE 419
//*             deck, or load module, and be able to                *   FILE 419
//*             determine just which version of the                 *   FILE 419
//*             source was used to build that object.               *   FILE 419
//*                                                                 *   FILE 419
//*             From the Berkeley manual page:                      *   FILE 419
//*                                                                 *   FILE 419
//*                 The what utility searches each specified        *   FILE 419
//*                 file for sequences of the form "@(#)" as        *   FILE 419
//*                 inserted by the source code control system.     *   FILE 419
//*                 It prints the remainder of the string following *   FILE 419
//*                 this marker, up to a NUL character, newline,    *   FILE 419
//*                 double quote, ``>'' character, or backslash.    *   FILE 419
//*                                                                 *   FILE 419
//*                 The following option is available:              *   FILE 419
//*                                                                 *   FILE 419
//*                 -s      Stop searching each file after the      *   FILE 419
//*                         first match.                            *   FILE 419
//*                                                                 *   FILE 419
//*                 Exit status is 0 if any matches were found,     *   FILE 419
//*                 otherwise 1.                                    *   FILE 419
//*                                                                 *   FILE 419
```
