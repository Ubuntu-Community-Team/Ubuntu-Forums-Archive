---
title: "error 13. I cannot start my windows!"
date: 2007-08-24
forum: Absolute Beginner Talk
---

### Post by Lina_inpas on 2007-08-24
Hihi,
I made a mistake when I was changing my menu.lst. I changed the root of windows to that of the Kubuntu, so now the system cannot induce itself into woindows and error 13: invalid or unsupported executable format occures. I don't know how to correct it.
in my menu.lst, all roots are now (hd0,3) while my wimdows root should  be (hd0,0).
I once tried to use the sentence ' dudo gedit /boot/grub/menu.lst' in the terminal to change the menu.lst back,but it said : sudo: gedit: command not found
Is anyone have some advice?
Thanks!

---

### Post by quinnten83 on 2007-08-24
if you did that in one of the prompt, without grpahical interface you well get that, try with sudo nano or perhaps sudo vi.

---

### Post by Lina_inpas on 2007-08-24
Hi,quinnten83!
Could you give me some more details? I am absolutly a new beginner.

---

### Post by mikeyphi on 2007-08-24
> **Lina_inpas said:**
> Hihi,
I made a mistake when I was changing my menu.lst. I changed the root of windows to that of the Kubuntu, so now the system cannot induce itself into woindows and error 13: invalid or unsupported executable format occures. I don't know how to correct it.
in my menu.lst, all roots are now (hd0,3) while my wimdows root should  be (hd0,0).
I once tried to use the sentence ' dudo gedit /boot/grub/menu.lst' in the terminal to change the menu.lst back,but it said : sudo: gedit: command not found
Is anyone have some advice?
Thanks!

gksudo gedit /boot/grub/menu.lst

is what you want

---

### Post by Lina_inpas on 2007-08-24
I logged onto my kubuntu, opened the terminal and typed what you told me but it said no such command.
If I typed it wiht LIVE CD, it said 'unrecognize command'
very strange!!!

---

### Post by mikeyphi on 2007-08-24
> **Lina_inpas said:**
> I logged onto my kubuntu, opened the terminal and typed what you told me but it said no such command.
If I typed it wiht LIVE CD, it said 'unrecognize command'
very strange!!!

Sorry - didn't realise you were in Kubuntu....gedit is for ubuntu!! There will be an equivalent for Kubuntu but that's not my OS...

---

### Post by quinnten83 on 2007-08-24
okay, 
start up your ubuntu normally
after the startup press ctrl+alt+F1, this will get you into a, well lets call it non graphical environment.
herein type your login name and then your password
then type in the command 

```
sudo nano /boot/grub/menu.lst
```

and you can edit the grub list in that terminal.

after you are done, you can press ctrl x to exit nano and ctr+alt+F7 to reenter a graphical environment, or you can press ctrl+aalt+BACKSPACE to restart the xserver.
maybe you will have better luck using nano.

---

### Post by quinnten83 on 2007-08-24
I think the alternative for kubuntu is kate.
or you can try in terminal, see iof nano is also available for kubuntu.
otherwise try if vi is available in terminal for kubuntu.

---

### Post by Lina_inpas on 2007-08-24
haha! nano works on Kubuntu!!!
I have fixed it! 
Thanks!:popcorn:

---

