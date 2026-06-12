---
title: "can´t print (using console in linux) when I connect to unix"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by socratesgdl on 2008-01-30
please help,

I have a pc with ubuntu installed, I open the konsole and using telnet access a unix server,but when I try to print a report it appears only in the window of konsole BUT NOT in the printer...



what can I do????




please!!!

---

### Post by eolson on 2008-01-30
Oh boy!  This has been YEARS!   And not even sure .... but have you tried cntrl p?   Old version of print scrn,  but it did a lot more on some systems.

---

### Post by Tenken on 2008-01-30
Are you trying to print to a printer attached to you local machine or one connect to the server your ssh'd into?

---

### Post by socratesgdl on 2008-01-30
I have one local printer installed. If I use SCREEN PRINTING it works properly.
The problem is when I am connected to the server unix, only if I request a report, it appears in the terminal   (if I use a PC with windows XP and use a terminal emulator it works perfectly).
THIS IS THE application (located in the unix server) that produces me headaches..



 xxmi25po.p           5.12.10 Reporte de Requisiciones       *         30/01/08
+------------------------------------------------------------------------------+
|         Requisicion: r30003                    A: r30003                     |
|   Fecha Requisicion:                           A:                            |
|     Fecha Requerida:                           A:                            |
|           Proveedor:                           A:                            |
|            Articulo:                           A:                            |
|             Almacen:                           A:                            |
|             Estatus:                           A:                            |
|            Solicita:                           A:                            |
|         Solo sin OC: no                                                      |
|  Incluir Ya Pedidos: N                                      Output: local    |
+------------------------------------------------------------------------------+


 IF I SELECT OUTPUT: "LOCAL"  IN PC WITH WINDOWS, using a terminal emulator,  the report appears in  the printer
IF I SELECT OUTPUT:  " LOCAL" IN UBUNTU BOX, using the konsole or terminal the report appears in the screen, AND I NEED IT IN THE PRINTER



PLEASE HELP ME!!
:-(

---

### Post by Tenken on 2008-01-30
What print command are you trying to use? Last time I did this (it's been quite a while) I think I used

```
lp /path/to/file
```

EDIT
This is another option I found
```
ssh -f username@server.org cat /path/to/report | lp 
```

---

### Post by socratesgdl on 2008-01-31
mmmm,,,let me explain again:
I have this hardware (working very well):


PC with windows, terminal emulator and  printer installed--->  unix server (running a QAD application)

(IP=192.168.0.53)                                                                          (IP=192.168.0.200)




If I connect using: telnet 192.168.0.200 and request a report of the application, the printer prints the report

I WANT TO CHANGE TO THIS:
PC with ubuntu, terminal and printer installed --->unix server (running a QAD application)

(IP=192.168.0.53)                                                                        (IP=192.168.0.200)

If I connect using telnet 192.168.0.200 and request a report of the application, the report appears in the terminal and NOT IN THE PRINTER


CAN ANYBODY HELP ME?

THANKS

---

### Post by socratesgdl on 2008-02-04
I solved this problem withe WINE software:
1.- Install WIne
2.- The folder containing TTERMPRO (tterm emulator) was installed in ubuntu
3.- run ttermpro using WINE






great!!

---

