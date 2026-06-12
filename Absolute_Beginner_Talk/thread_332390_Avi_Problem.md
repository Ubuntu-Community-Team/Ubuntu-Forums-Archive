---
title: "Avi Problem"
date: 2007-01-06
forum: Absolute Beginner Talk
---

### Post by pipin on 2007-01-06
Hello. When I intend to watch an avi file using VLC, VLC just displays one second and disappears. 
The terminal output is;
> main warning: can't store message (Invalid or incomplete multibyte or wide character): found Chunk fourcc:019187b0 (
X Error of failed request:  BadAlloc (insufficient resources for operation)
  Major opcode of failed request:  141 (XVideo)
  Minor opcode of failed request:  19 ()
  Serial number of failed request:  89
  Current serial number in output stream:  90
Thanks in advance.

---

### Post by Shatrat on 2007-01-06
Looks like this is a problem with xv video output.  
What graphics hardware do you have and have you installed the binary drivers for it?

edit
A quick fix would be to try other output settings in the VLC preferences, Preferences -> Video -> Output Modules (with the advanced tick box checked)
You should get xv working though imo, if that's the problem.

---

### Post by pipin on 2007-01-06
> **Shatrat said:**
> Looks like this is a problem with xv video output.  
What graphics hardware do you have and have you installed the binary drivers for it?

Hi . Thanks for the reply. I dont actually have a graphic card. It is onboard INTEL Graphic Adapter Chip..

---

### Post by pipin on 2007-01-06
> **Shatrat said:**
> Looks like this is a problem with xv video output.  
What graphics hardware do you have and have you installed the binary drivers for it?

edit
A quick fix would be to try other output settings in the VLC preferences, Preferences -> Video -> Output Modules (with the advanced tick box checked)
You should get xv working though imo, if that's the problem.

Sorry but on VLC , I have an empty menu under Video option. There is nothing to be edited.

---

