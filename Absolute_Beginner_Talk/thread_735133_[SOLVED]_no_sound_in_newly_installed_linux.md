---
title: "[SOLVED] no sound in newly installed linux"
date: 2008-03-25
forum: Absolute Beginner Talk
---

### Post by bhadotia on 2008-03-25
we just installed new ubuntu on my friends lenevo y410 laptop but there is no sound. can anybody help us.:confused:

---

### Post by olskar on 2008-03-25
Can you put this in a terminal and post the output:

lspci | grep audio

---

### Post by superprash2003 on 2008-03-25
hope this works [http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html](http://prash-babu.blogspot.com/2008/02/sound-problems-in-ubuntu-gutsy-710.html)

---

### Post by northern lights on 2008-03-25
Can you please post the output of ```
cat /proc/asound/cards
```

Thanks.

[EDIT]Late. lspci works as well - anyways give some specs please.[/EDIT]

---

### Post by bhadotia on 2008-03-25
hello, northernlights


akash@akash-laptop:~$ su
Password: 
root@akash-laptop:/home/akash# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8300000 irq 22
root@akash-laptop:/home/akash# cat /proc/asound/cards
   
    this is the out put

---

### Post by bhadotia on 2008-03-25
hello, olskar

there is no out put to this command

---

### Post by bhadotia on 2008-03-25
hello superprash2003 i tried the solutions given on that web page but that did not work...

---

### Post by northern lights on 2008-03-25
Intel High Definition Audio Controllers have proven quite problematic, this [wiki]("https://wiki.ubuntu.com/Gutsy_Intel_HD_Audio_Controller") might help.

I got it done on a Dell Latitude D630, I'm sure one of the many workarounds works for you. It's a bitch though, granted...

---

### Post by sberan on 2008-03-25
[http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/](http://linuxtechie.wordpress.com/2007/10/19/getting-intel-ich8-family-rev-3-sound-card-to-work-in-gutsy/)

I have a y410, I believe this is what fixed it.

---

### Post by bhadotia on 2008-06-22
Found the solution on google . Look here:
[URL="http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html"]http://linuxondesktop.blogspot.com/2007/12/getting-sound-to-work-on-your-ubuntu.html 
[/URL]

---

### Post by carib909 on 2008-06-23
Here is my output:

evan@ubuntu:~$ cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xfdff4000 irq 20
 1 [U0xd8c0x0c     ]: USB-Audio - USB Device 0xd8c:0x0c
                      USB Device 0xd8c:0x0c at usb-0000:00:1a.1-2, full speed
I get sound on my USB headset when playing music, but I cannot switch to the speakers. The speakers work when Ubuntu loads up.







> **bhadotia said:**
> hello, northernlights


akash@akash-laptop:~$ su
Password: 
root@akash-laptop:/home/akash# cat /proc/asound/cards
 0 [Intel          ]: HDA-Intel - HDA Intel
                      HDA Intel at 0xf8300000 irq 22
root@akash-laptop:/home/akash# cat /proc/asound/cards
   
    this is the out put

---

### Post by bhadotia on 2008-06-23
Do you have lenevo pc (laptop actually)? And did you follow the link I gave above? 


Well , if you did follow the link you should have read that there still some issues with the method given therein . Those are :that headphones don't have sound. As you use usb headphones you might get sound working on them. But, I think because of the loopholes in the method the speakers might stop working after  you plug-in your head phones.

Try this: 
Suspend your computer after using your headphones (and plugging them out), and then again start your computer. The speakers might work now. If this works ,it is better  than restarting your computer to get the sound back.

---

