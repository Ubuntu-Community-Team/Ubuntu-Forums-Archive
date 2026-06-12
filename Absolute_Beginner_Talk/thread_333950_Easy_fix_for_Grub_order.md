---
title: "Easy fix for Grub order"
date: 2007-01-08
forum: Absolute Beginner Talk
---

### Post by Goth Mneph on 2007-01-08
[B]I'm still pretty new to the Ubuntu/Kubuntu family, but i just learned a neat little trick to allow my grub to pick the windows automatically for the others in my family.

i copied someone else's post to get into the grub edit.  not sure if you have to go this way but i did.  i copied each line and pasted them in to the terminal one at a  time.[/B]

cat /boot/grub/menu.lst (hit Enter)

sudo cp /boot/grub/menu.lst /boot/grub/menu.lst.bak  (hit Enter)

sudo gedit /boot/grub/menu.lst  (hit Enter)

[B]after i entered the last line and hit enter it took me to a edit screen.

now here's where it gets easy.  
i figured that every thing that begins with the double dollar signs "##"  means nothing to the computer, they're just reference.

look for some lines that looks something like this.[/B]

# You can specify 'saved' instead of a number. In this case, the default entry
# is the entry saved with the command 'savedefault'.
# WARNING: If you are using dmraid do not change this entry to 'saved' or your
# array will desync and will not let you boot your system.
default         0

## timeout sec
# Set a timeout, in SEC seconds, before automatically booting the default entry
# (normally the first entry defined).
timeout         10

**now count the entries of your operating systems.  I think each place that starts with "title" begins a new OS entry,**

(examples)
title           Microsoft Windows XP Professional
root            (hd0,0)
savedefault
makeactive
chainloader     +1

title           Ubuntu, kernel 2.6.15-27-686
root            (hd1,1)
kernel          /boot/vmlinuz-2.6.15-27-686 root=/dev/hdb2 ro quiet splash
initrd          /boot/initrd.img-2.6.15-27-686
savedefault
boot


[B]not sure but, mine showed two entries for windows XP one at title # 6 and one at title # 7.  i put in 6 next to the word "default", first and saved and rebooted, then i found out it was actually 7.  you can also change how long it takes for the Grub to choose the "default" OS at the "timeout" spot.

Hope this helps any other of you noobs like me.
good luck and live happy in Linux.[/B]

---

