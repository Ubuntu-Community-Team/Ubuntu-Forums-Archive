---
title: "Usplash won't load"
date: 2008-01-11
forum: Absolute Beginner Talk
---

### Post by paranoiahax on 2008-01-11
Hi, I was referred to come here from General Help because apparently you get better help on this board. 

Anyway, here's the problem;

I'm experiencing some trouble at my Usplash screen, I load grub as usual, select ubuntu, and it goes to the usplash screen, and loads marginally (like a bar of orange can be seen right at the beginning) but freezes. I check what's going on by pressent alt + ctrl + f1 and I get this:

> 
Starting up...
Loading, please wait...
usplash: Setting mode 1280x1024 failed
usplash: Setting mode 1152x864 failed
usplash: Using mode 1024x768


and just stays that way.

Now I was told that it's to do with my usplash so I have to : sudo gedit /media/disk/etc/usplash.conf (the place where my HD is mounted to) and edit it to 1024x768.

Then I need to do sudo update-usplash-theme usplash-theme-ubuntu.

But the thing is, this command will do it from my live cd seen as though i'm booting in live.

so i try to go into recovery mode and it only gives me a simple shell which i can't do much with, especially what i need to do!

I've tried leaving it to boot up the usplash for about 10 minutes, and eventually it does something.. it simply gives me the recovery shell LOL so i'm at my wit's end, been trying to sort this out for ages lol. Has anyone got any ideas?

Regards, para

---

### Post by paranoiahax on 2008-01-11
any body..? :(

---

### Post by mister_pink on 2008-01-11
Well, I don't know anything about the problem but those commands certainly can be run in recovery mode, with the exception of gedit - just replace that with nano! You can drop the sudo's too in recovery mode, you have root privileges automatically.

---

### Post by John.Michael.Kane on 2008-01-11
You can try editing the grub menu at system startup.

Press 'esc' this will bring you into the main grub list .

   Highlight the line you want to edit this would be your kernel line. with the <Up> and <Down>Keys (arrow keys)
   press 'e' to edit the selected line.
   You will then see something along the lines of the example below
   ```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash 

``` 

  Next add vga=791 to the end kernel line being edited.

  While editing you may want to delete the options 'quiet' or 'splash' with the delete key
   press <Esc> to leave the edit mode and
   press <b> to boot

  This should allow you to complete the boot process, Also the edit  only affects system startup To make the edit permanent you would have to edit the /boot/grub/menu.lst.

---

### Post by paranoiahax on 2008-01-11
mmm okay i'll give it a go lol. but am i mistaken or does recovery mode create a new root, because it doesn't display my home folder anywhere in recovery.. is that supposed to happen?

i'll give it a go, but i dunno if i can remember the commands lol. i'll write it down somewhere.

---

### Post by paranoiahax on 2008-01-11
> **John.Michael.Kane said:**
> You can try editing the grub menu at system startup.

Press 'esc' this will bring you into the main grub list .

   Highlight the line you want to edit this would be your kernel line. with the <Up> and <Down>Keys (arrow keys)
   press 'e' to edit the selected line.
   You will then see something along the lines of the example below
   ```
kernel /boot/vmlinuz-2.6.20-15-generic root=UUID=fccafcc7-d7cc-4594-9459-a8f0db7b9f7f ro quiet splash 

``` 

  Next add vga=791 to the end kernel line being edited.

  While editing you may want to delete the options 'quiet' or 'splash' with the delete key
   press <Esc> to leave the edit mode and
   press <b> to boot

  This should allow you to complete the boot process, Also the edit  only affects system startup To make the edit permanent you would have to edit the /boot/grub/menu.lst.

hey thanks, this seemed to do something positive... my menu.lst now looks like this:

```
title		Ubuntu
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
password --md5  *****************************
```

does that look right?

now when i boot it, the screen just goes blank and does nothing, and i leave it for about 5 minutes and still does nothing so i restart.

is this a good thing? lol

thanks in advance, para

---

### Post by John.Michael.Kane on 2008-01-11
> **paranoiahax said:**
> hey thanks, this seemed to do something positive... my menu.lst now looks like this:

```
title		Ubuntu
root		(hd0,3)
kernel		/boot/vmlinuz-2.6.22-14-generic root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro vga=791
initrd		/boot/initrd.img-2.6.22-14-generic
quiet
password --md5  *****************************
```

does that look right?

now when i boot it, the screen just goes blank and does nothing, and i leave it for about 5 minutes and still does nothing so i restart.

is this a good thing? lol

thanks in advance, para
That should have allowed the boot process to continue. 

Try adding quiet splash back to the line.
You should have something like below.
```
root=UUID=919e75f9-2aee-4076-8b67-5e95f9a42bc1 ro quiet splash  vga=791
```

Also what are your system spec's? eg video card mother board monitor etc.

---

