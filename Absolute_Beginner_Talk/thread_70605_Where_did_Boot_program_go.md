---
title: "Where did Boot program go?"
date: 2005-09-30
forum: Absolute Beginner Talk
---

### Post by alime on 2005-09-30
I'm working on breezy and it had a update.
so i did the update it rebooted and i seen it took out my XP option in my boot menu. No problem ill use that boot utility again and add it.
let see i go to System > Administration > Boot....Boot...
that boot utility is gone..
i was wondering how to put get it back.
any help would be great thanks
"A"

PS
i looked for it in synaptic packager manager but it was not called boot

---

### Post by alime on 2005-09-30
[IMG]http://www.pipelineyouth.com/missing.gif[/IMG]
I have lost that icon.

---

### Post by PsyberOneZero on 2005-09-30
Here's a post from the Breezy Development Forum:
[http://www.ubuntuforums.org/showthread.php?t=70005](http://www.ubuntuforums.org/showthread.php?t=70005)

It looks like they took it out **_temporarily_** to squash some bugs.  Hopefully it will be back soon.

---

### Post by alime on 2005-09-30
[QUOTE=PsyberOneZero]Here's a post from the Breezy Development Forum:
[http://www.ubuntuforums.org/showthread.php?t=70005](http://www.ubuntuforums.org/showthread.php?t=70005)
It looks like they took it out **_temporarily_** to squash some bugs.  Hopefully it will be back soon.[/QUOTE]

awesome thanks
i thought i was going crazy.
i guess that is why you dont depend on beta as your main machine.
I learn... 
Thanks again
"A"

---

### Post by PsyberOneZero on 2005-09-30
[QUOTE=alime]i guess that is why you dont depend on beta as your main machine.[/QUOTE]
I'm a little touched in the head so I do use Breezy as my one and only, but new(er) users should stick with the stable version.
Breezy will be there soon - 2ish weeks.

---

### Post by alime on 2005-09-30
[QUOTE=PsyberOneZero]I'm a little touched in the head so I do use Breezy as my one and only, but new(er) users should stick with the stable version.
Breezy will be there soon - 2ish weeks.[/QUOTE]
K 
Thanks

---

### Post by grnorton on 2005-10-02
This happened to me too! I am in the process of migrating from OS/2 to Linux and have OS/2 installed on the first partition
/dev/hda1
so how do I edit the GRUB menu list to add this back to my grub boot options?
I am *very* new so please hold my hand and dont assume anything ;) :)   in any replies.
cheers
Graham

---

### Post by PsyberOneZero on 2005-10-02
[QUOTE=grnorton]This happened to me too! I am in the process of migrating from OS/2 to Linux and have OS/2 installed on the first partition
/dev/hda1
so how do I edit the GRUB menu list to add this back to my grub boot options?
I am *very* new so please hold my hand and dont assume anything ;) :)   in any replies.
cheers
Graham[/QUOTE]

**1. Open a root created gedit**
```
Applications->System Tools->Run as different user
```
type: gedit
make sure the user is set to root
click OK
Enter your password when prompted

**2. Open /boot/grub/menu.lst**
Once in gedit click open
browse to **/boot/grub/menu.lst**
OPEN
You should see something like this at the bottom of the file
```
## ## End Default Options ##
title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default 
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/sda5 ro console=tty0 quiet splash
initrd		/boot/initrd.img
savedefault
boot
title		Ubuntu, kernel 2.6.12-9-amd64-k8 Default (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz root=/dev/sda5 ro console=tty0 single
initrd		/boot/initrd.img
boot
title		Ubuntu, kernel 2.6.12-9-amd64-k8 
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sda5 ro console=tty0 quiet splash
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
savedefault
boot
title		Ubuntu, kernel 2.6.12-9-amd64-k8 (recovery mode)
root		(hd0,4)
kernel		/boot/vmlinuz-2.6.12-9-amd64-k8 root=/dev/sda5 ro console=tty0 single
initrd		/boot/initrd.img-2.6.12-9-amd64-k8
boot
title		Ubuntu, memtest86+
root		(hd0,4)
kernel		/boot/memtest86+.bin  
boot
### END DEBIAN AUTOMAGIC KERNELS LIST

```
You just need to add a few lines after this to have OS/2 in your boot menu for good
```

title		OS/2 Warp
root		(hd0,0)
makeactive
chainloader +1
```
make sure you put those 4 lines after this line **AFTER **
```
## END DEBIAN AUTOMAGIC KERNELS LIST
```
here's how it should look
```
### END DEBIAN AUTOMAGIC KERNELS LIST

title		OS/2 Warp
root		(hd0,0)
makeactive
chainloader +1
```

then save your file.
Next time you boot up you sould be able to go play with all the warp-y goodness you can handle

---

### Post by grnorton on 2005-10-04
A thousand thanks!  Never have I had my hand held so gently and yet so strobgly and It all went perfectly and now I am booting to either system!

thanks again

Graham

---

