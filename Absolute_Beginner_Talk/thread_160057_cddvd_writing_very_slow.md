---
title: "cd/dvd writing very slow"
date: 2006-04-14
forum: Absolute Beginner Talk
---

### Post by joshrobinson on 2006-04-14
my dvdr/cdr writer is
48x cdr, and 16x dvd-5

but i only get speeds around 1.5x with dvd's and 10-25x for cdr's

ive tried both k3b and gnomebaker

both the same thing, is this a hardware problem?
its a samsung drive

---

### Post by Perfect Storm on 2006-04-14
Have you enable DMA for your Drives?

---

### Post by joshrobinson on 2006-04-14
[QUOTE=Artificial Intelligence]Have you enable DMA for your Drives?[/QUOTE]

could you point me in the right direction ](*,) 

is that in the burning programs options?

---

### Post by Perfect Storm on 2006-04-14
Check first if it is enable, assuming your DVD drive is cdrom or just change it if it's your second drive to cdrom1:

```
sudo hdparm /dev/cdrom
```

If DMA=off then

```
sudo gedit /etc/hdparm.conf
```

and add in the buttom:
```
/dev/cdrom {
        dma = on
}
```

reboot

---

### Post by joshrobinson on 2006-04-14
ahh much better :-D 

thanks so much!

---

### Post by underwater on 2006-04-14
What if it doesn't mention DMA on or off?

---

### Post by joshrobinson on 2006-04-14
[QUOTE=underwater]What if it doesn't mention DMA on or off?[/QUOTE]

its in there for me.. 3rd line down using_dma
but you can edit the file like that was said above to turn it on if it doesnt mention it for you


joshua@ubuntu:~$ sudo hdparm /dev/cdrom

/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 **using_dma**    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)

---

### Post by dcstar on 2006-04-16
[QUOTE=joshrobinson]
.......
/dev/cdrom:
 IO_support   =  0 (default 16-bit)
 unmaskirq    =  0 (off)
 **using_dma**    =  1 (on)
 keepsettings =  0 (off)
 readonly     =  0 (off)
 readahead    = 256 (on)[/QUOTE]
The first two options can (usually) also be tweaked for performance gains, try:
```
hdparm -c3 /dev/cdrom
hdparm -u1 /dev/cdrom
```
and see if things improve.

Note that these can also improve your hard drive performance as well.

---

### Post by Roadrunner777 on 2006-04-30
Wow, I thought I was stuck with slow burning... thank you so much for posting this fix!

---

### Post by nalmeth on 2006-04-30
A.I. is the man :)

---

