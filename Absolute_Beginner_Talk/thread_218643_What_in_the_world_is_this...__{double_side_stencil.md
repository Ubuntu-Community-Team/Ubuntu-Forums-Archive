---
title: "What in the world is this... ? {double side stencil}"
date: 2006-07-18
forum: Absolute Beginner Talk
---

### Post by Average_Joe on 2006-07-18
I suspected my ATI Radeon 9600 128MB video card was not talking to my Ubuntu install.  So I typed in the command: glxinfo | grep rendering

What you see below is what I got back.  What does it mean?


username@username-ubuntu:~$ glxinfo | grep rendering
*********************************WARN_ONCE*********************************
File r300_state.c function r300Enable line 456
TODO - double side stencil !
***************************************************************************
No ctx->FragmentProgram._Current!!
direct rendering: Yes
username@username-ubuntu:~$

---

### Post by Afishionado on 2006-07-18
It's a feature of the video card that the driver doesn't support yet. Basically, the drivers aren't finished yet. :) 

"direct rendering: yes" implies that everything is working. Any specific problems you're having?

---

### Post by Average_Joe on 2006-07-18
Thanks for the reply.  Later, I used a web how-to to install the ATI drivers pacled with Ubuntu for Radeon cards in the 8500 and up series.  (Mine is a  Radeon 9600.)  And now when I do the glxinfo | grep rendering command, it does give me the simple response you indicated.  Thanks again.

---

### Post by kurniawands on 2006-07-18
Thanks god.... My 9200 pro 128Mb is working very well heheheheheh...:o :-D :-D think it's already recognized hehehehe...

---

### Post by Average_Joe on 2006-07-18
To kurnia --
My 9600 was also recognized and SOME of its functionality was in use, but not all of it.  What was your output/return when you did this command in the terminal?

---

