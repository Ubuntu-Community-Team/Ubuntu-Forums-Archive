---
title: "Help with screen resolution please?"
date: 2007-06-13
forum: Absolute Beginner Talk
---

### Post by ebony_rogue on 2007-06-13
Just started my system this morning but the screen resolution seems to have changed. The text is huge, the windows don't fit into the screen. So tried to change the resolution through sscreen resolution preferences but only have the 640x480 option. Any assistance will be appreciated. Try to respond in lay-man's terms, i'm the noobiest noob.

---

### Post by DeuceII on 2007-06-13
> **ebony_rogue said:**
> Just started my system this morning but the screen resolution seems to have changed. The text is huge, the windows don't fit into the screen. So tried to change the resolution through sscreen resolution preferences but only have the 640x480 option. Any assistance will be appreciated. Try to respond in lay-man's terms, i'm the noobiest noob.

I had this a week ago to.

In a console type -

***sudo dpkg -Reconfigure-phigh Xserver-xorg ***

and then press ctrl-alt-backspace.

HTH

---

### Post by phr0ze on 2007-06-13
What gets me is if I do something to make X start failing, it can't be smart enough to ask me if I want to try an automated fix (like this one).

The amount of 'help me, x wont start' posts would be greatly reduced.

---

### Post by vigleik on 2007-06-13
> **phr0ze said:**
> What gets me is if I do something to make X start failing, it can't be smart enough to ask me if I want to try an automated fix (like this one).

The amount of 'help me, x wont start' posts would be greatly reduced.

They are working on it. I believe future versions of xorg will be much smarter. At least I hope....

---

### Post by ebony_rogue on 2007-06-17
Thanks for your solution but, didn't work, this is what I got:
dpkg: conflicting actions --contents and --control

Type dpkg --help for help about installing and deinstalling packages [*];
Use `dselect' or `aptitude' for user-friendly package management;
Type dpkg -Dhelp for a list of dpkg debug flag values;
Type dpkg --force-help for a list of forcing options;
Type dpkg-deb --help for help about manipulating *.deb files;
Type dpkg --licence for copyright licence and lack of warranty (GNU GPL) [*].

Options marked [*] produce a lot of output - pipe it through `less' or `more' !
After pressing cntrl-alt-backspace, there was no difference. Any other solution?

---

