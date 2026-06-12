---
title: "Non-urgent: Installing software from cd-roms / wiki questions for Xubuntu"
date: 2007-04-07
forum: Absolute Beginner Talk
---

### Post by Pseudonomous on 2007-04-07
Hello,

This is my first time post here, so I'd like to thank everyone providing technical
assistance in these forums, as well as the programmers and other developers
whose combined efforts have produced a wonderful product.

Background:

I'm running Xubuntu 6.10 on a laptop with an intel celeron processor.

But know my questions:

Aside = It's really questions (1) and (4) I care about, I'm pretty sure I can find the answers to the other by searching the Ubuntu and Xfce wiki pages.

(1) I recently installed Xubuntu on my laptop, and I'm trying to build up a suite of applications that I will need, amongst them I need some LaTeX software, so I downloaded TeXlive2007 on another computer, stuck it on a CD and attempting very unsuccessfully to run the install program.  When I tried to 'sudo' the install command, the terminal would respond 'permission denied'.  I tried to change my
file permissions, (using a helpful tutorial from the Ubuntu wiki), but this had no
discernable effect.  

In the end what worked was me copying the files to the hard drive, then running the install command in the copied directory.  Which worked just fine, the only issue is one of efficiency, it seems like the install program SHOULD be able to run off the CD.

Now the terminal kept saying something about changing permissions on "Read only Device" when I tried to adjust the file permissions so I could execute the file.  Is there something in my configuration that I need to change so I can run programs off of a CD?

2) Xubuntu comes with a firefox Launcher next to the "applications" menu, but I can't figure out how to add more launchers to the bar... could someone tell me how to do this?

3) It seems that both bottons on the mouse surraget interface for my laptop have the same effect, is there a way for me to make the 'right click' do something different?

4) The ubuntu wiki seems far more comprehensive than the Xubuntu wiki... what kind of things should I be searching the Ubuntu wiki for... and what sort of things should I be searching the xfce site for?

5) Are the xffm and Thunar file browsers the same software... ore are they different?

Thank you in advance for taking the time to answer my questions.

---

### Post by 3rdalbum on 2007-04-07
1. You must copy the application to your hard drive first. Having to explicitly set the "execute" permission is a security feature. These permissions are stored within the filesystem that houses the application file; of course, since it's on a CD, the permissions cannot be stored.

5. Thunar is the latest file browser, and is very good. Xffm is very unintuitive and difficult to use, but there are some good features. My suggestion is to use Thunar unless you havea  pressing need not to.

The other questions had me stumped, unfortunately.

---

### Post by Pseudonomous on 2007-04-13
Thank you very much for your help.

It turns out that I actually am having some issues with my installation of TeX live 2007, but I will either take this up with TUG or simply use TeTeX, which despite being older, seems to run just fine.


Sorry fo the delay in my reply.

---

