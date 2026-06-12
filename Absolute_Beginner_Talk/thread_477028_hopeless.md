---
title: "hopeless"
date: 2007-06-17
forum: Absolute Beginner Talk
---

### Post by alanc on 2007-06-17
:p Hi.  I am trying to instal Ubuntu on to a 2nd HDD, but i cannot get anything to appear on screen.
        I know the boot from CD drive is configured right, because i have run a live cd and it has worked ok.
       Could someone please help me, it is so frustrating.
                                           Regads     alanc:(

---

### Post by p_quarles on 2007-06-17
Have you tried installing it from the alternate cd? That's worked for me in the past, and I would recommend it as a next step.

---

### Post by alanc on 2007-06-17
:p Hi.  No, i cannot get it to boot from the alternate cd.
                               Regards    alanc:(

---

### Post by fdrake on 2007-06-17
probably it's the cd the problem:
how did you burn the cd image?
what speed did you burn it at?

---

### Post by alanc on 2007-06-17
:p Hi.   I ordered the cd from there website, and they tell me the cd is OK.
                                                 Regards    alanc:(

---

### Post by p_quarles on 2007-06-17
> **alanc said:**
> :p Hi.   I ordered the cd from there website, and they tell me the cd is OK.
                                                 Regards    alanc:(
That doesn't sound promising, I'm kind of at a loss here, but I'll try my best. 

1) What are the system specs?

2) What happens when you hit the "install" icon from the live CD? Does it fail to recognize the second hard drive, or does it do nothing at all?

---

### Post by fdrake on 2007-06-17
it's very strange that even the alternate cd doesn't work. do this cd works in another machine, can you try them on other computers.  what kind of computer do you use ? mac, pc, 64bit amd??? ar you sure the cd are the right one's for your computer?

---

### Post by fdrake on 2007-06-17
> **p_quarles said:**
> That doesn't sound promising, I'm kind of at a loss here, but I'll try my best. 

1) What are the system specs?

2) What happens when you hit the "install" icon from the live CD? Does it fail to recognize the second hard drive, or does it do nothing at all?

i am lost too, so you can boot with the live cd then?? but you are unable to install ubuntu... right??

---

### Post by nickaj on 2007-06-17
As an equally hopeless shot in the dark, what's your hardware like?  I tried installing Ubuntu on an older laptop and it got almost completely frozen, blank screen for long periods.  After waiting hours just for a window to open i tried Xubuntu instead - worked perfectly.

---

### Post by empthollow on 2007-06-17
you can boot from a live cd as well as install but you have to have the right cd for your motherboard architechure, ie. 64bit, ppc, macbook, - if you don't know you probably have a i386.  otherwise post your model here and one of us will look it up.

---

### Post by alanc on 2007-06-18
:p Hi.   I am not sure what you are after, but here goes,the motherboard is a AsusP4S800-MX SE   
      Pentium 4 processor.  SiS661FX/964 chipset,and supports AGP  8X, 800MHz front side bus, and DDR400.
      Hope this is what you required.
                                                              Regards     alanc:)

---

### Post by empthollow on 2007-06-18
ok, i'm not sure exactly how far you got in the install process.  what you need to do is get a copy of the i386 live cd, boot it, double click on the install icon on the desktop.  this will open the installer. somewhere in here you should be able to choose the disk and whether to use standard or custom partitioning.  let me know where in this process you get stuck.

---

### Post by alanc on 2007-06-19
:p Hi.   Where would i get a copy of i386 cd. I am only a bit of a beginner at all of this, so i am sorry if i seem
            to ask some silly questions.
                                                                 Regards     alanc:(

---

### Post by fdrake on 2007-06-19
to download
[http://www.ubuntu.com/getubuntu/download](http://www.ubuntu.com/getubuntu/download)
select desktop version, standard personal computer and your location

to purchase
[http://www.ubuntu.com/getubuntu/purchase](http://www.ubuntu.com/getubuntu/purchase)

---

### Post by alanc on 2007-06-20
:p Hi.   I can boot from the live cd but i cannot install from the live cd.  When i put the  Install cd in and boot up, 
        i get nothing it just goes into Windows.
                                                                             Regards     alanc:(

---

### Post by alanc on 2007-06-20
> **fdrake said:**
> i am lost too, so you can boot with the live cd then?? but you are unable to install ubuntu... right??

:pHi.    There is no install button on the live cd, or i cannot find one.
                                        Regards    alanc:(

---

### Post by Afrikprophet on 2007-06-20
> **alanc said:**
> :p Hi.   I can boot from the live cd but i cannot install from the live cd.  When i put the  Install cd in and boot up, 
        i get nothing it just goes into Windows.
                                                                             Regards     alanc:(

may be a stupid question but were you booting from the CD?

---

### Post by p_quarles on 2007-06-20
The install icon should be in the upper left-hand corner of your screen. You said earlier that the live CD worked. Is this a new CD? What exactly happens when you boot from it?

---

### Post by empthollow on 2007-06-21
there may be a bios setting you need to change for on my laptop i have to press f12 for boot options and tell the computer to boot off cd.

---

### Post by alanc on 2007-06-24
:p Hi.  I have got a cd Red Hat from a book that i just bought. Can someone please explain to me how i go
        about installing it on my external hard drive G:/    when i try to install it it keeps going to HDD  C:/
       I have downloaded things before, and it always gives you an option of which  HDD  that you want to
      install it on, but on this cd it doesn,t.
                                                                     Regards     alanc:(

---

### Post by fdrake on 2007-06-24
> **alanc said:**
> :p Hi.  I have got a cd Red Hat from a book that i just bought. Can someone please explain to me how i go
        about installing it on my external hard drive G:/    when i try to install it it keeps going to HDD  C:/
       I have downloaded things before, and it always gives you an option of which  HDD  that you want to
      install it on, but on this cd it doesn,t.
                                                                     Regards     alanc:(

what red hat version are u talking about. i am not an experienced red hat user but i am pretty sure that the book u bought should say something about it. check this [thread]("http://www.linuxquestions.org/questions/showthread.php?p=2796135") it's very similar to yours, and may give u some nice advices why and why not to choose red hat.

---

### Post by L8erG8er on 2007-06-24
alanc:

Is your computer set up to boot from the CD or DVD drive first?  If it isn't, you're never going to get the install working.

It sounds to me like your machine is booting HDD c: first, which is why it goes to Windows first.  I doubt there is anything wrong with your install disk.

---

### Post by fdrake on 2007-06-24
[here]("http://www.google.com/url?sa=t&ct=res&cd=4&url=http%3A%2F%2Fjoule.bu.edu%2F~hazen%2FLinuxCluster%2Fe1447_p4s800-mx.pdf&ei=bSZ_Ru7kHZioeqTLjbYK&usg=AFQjCNE0gdBWzPdDQuA-hb5KJ4YUhLQPzA&sig2=W6c8K4coypduHIR7ONFgOQ") is the manual for ur computer model . take a look at it and at the bios settings . read the Boot Sequence part.page 58

---

### Post by Happy_Man on 2007-06-24
When you boot up your computer, there will first be a screen with your manufacturer's logo. Somewhere on that screen will say "such and such key = boot order". Press that button and select the CD drive *when the LiveCD is in there*. It will boot the LiveCD. I know you say that you have tried it, do it again just so we can be sure it's not you but the CD that is having problems.

---

### Post by alanc on 2007-06-25
:p Hi.   I have just received my new cd of Ubuntu 7.04 and installed it. That all went OK, now i cannot get my emails to work, revolution downloaded OK, but i cannot get emails thru. Thebar
  at the top has only  NEW highlighted, send/ receive and print -delete and all the others are
    dulled out, and nothing happens when you click on them. Can someone please help me out
    or direct me to somewhere i can read about it, i have looked but cannot find anything
    helpful.
                                                        Regards    alanc;)

---

