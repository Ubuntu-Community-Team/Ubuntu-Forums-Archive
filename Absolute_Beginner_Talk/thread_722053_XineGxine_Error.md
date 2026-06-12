---
title: "Xine/Gxine Error"
date: 2008-03-12
forum: Absolute Beginner Talk
---

### Post by sraisaac on 2008-03-12
1. This is the error I get, Also I have installed the following: 

Xine/Gxine
Mplayer
VLC
all the associated lib files to go with them. *I think* 

2. Not sure how to get all the codecs for divx, xvid, quicktime. I searched SPM and looked for everything i could find related to these codecs and installed them. Perhaps I'm missing some? 

3. Also, I don't know if its related to codec problems but I can open AVI files with VLC but i get a blue Hue over everything. I was also getting the video offset in the viewer but i found that deinterlace fixed that. Not sure if thats the right path to fix that problem.

4. Also i get allot of flicker. As in each frame jumps back and forth slightly. Any idea for the cause of this? I know theres alot of problems in one post but I think them may all be related. IE, i did something wrong or didn't install something. 



[COLOR="Blue"]sraisaac@sraisaac-linux:~$ gxine
The program 'gxine' received an X Window System error.
This probably reflects a bug in the program.
The error was 'BadMatch (invalid parameter attributes)'.
  (Details: serial 328 error_code 8 request_code 141 minor_code 14)
  (Note to programmers: normally, X errors are reported asynchronously;
   that is, you will receive the error a while after causing it.
   To debug your program, run it with the --sync command line
   option to change this behavior. You can then get a meaningful
   backtrace from your debugger if you break on the gdk_x_error() function.)
sraisaac@sraisaac-linux:~$ 
[/COLOR]


[COLOR="Blue"]sraisaac@sraisaac-linux:~$ xine
This is xine (X11 gui) - a free video player v0.99.5.
(c) 2000-2007 The xine Team.
X Error of failed request:  BadMatch (invalid parameter attributes)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  14 ()
  Serial number of failed request:  2404
  Current serial number in output stream:  2404
sraisaac@sraisaac-linux:~$ [/COLOR]

---

### Post by Dark Star on 2008-03-12
> 2. Not sure how to get all the codecs for divx, xvid, quicktime. I searched SPM and looked for everything i could find related to these codecs and installed them. Perhaps I'm missing some?

[How to : Enable Multimedia Suport in Ubuntu 7.10.]("http://tuxenclave.wordpress.com/2008/01/03/how-to-enable-multimedia-suport-in-ubuntu-710/")
I have written this guide and hope it will help you regarding you codec problem :)

---

