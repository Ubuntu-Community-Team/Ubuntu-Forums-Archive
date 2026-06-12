---
title: "[FIX] Freezing ,BUG Soft Lockup Cpu .. Stuck For.. ! Or GPU Manager Errors. AMD64"
date: 2015-12-27
forum: Any Other OS
---

### Post by P0c-TeaM on 2015-12-27
good Afternoon guys..

    how is everybody ? good ? ok

    (tried on kali linux 2.0 ubuntu 14.. linux Mint 17 etc.. all 64Bit)

    Note: Please Post Your Feedback in here .

If you have any problems with installation or getting to GUI or you had error's similar to this:
```
Feb 10 02:58:09 shannon kernel: [44668.100003] BUG: soft lockup - CPU#1 stuck for 22s! [irqbalance:972]
```

OR

```
Feb 10 02:58:09 shannon kernel: [44668.100005] BUG: soft lockup - CPU#3 stuck for 21s! [gpu-manager:]
```
or you faced the splash screen freezing problem..
or you have two graphic cards especially Nvidia GTX960M or any NEW Nvidia card moudel ..Then this Fix maight work for you "it really worth a try"

actually me and my team were so away from hacking and this field  since 2011 .. but i have seen this NEW distro(kali)  and i said why not try it  out and remember the nice old hacking days ?!

    really  since BackTrack and i always had hardware problems with it ..

    i bought a new laptop for my brother (MSI GE62 6QD Apache Pro Intell  I7 6th Gen X64Bit) its for gaming but i was trying to install kali on  it . it just does not want to get into the live cd giving me a lot of  errors .. this laptop has UEFI and secure boot and windows10 (i hate it  by the way) ok .. enough with talking..

    first you need a cup of coffee or tee and you need to be in a good mode : D

    ################################
    1/ start your laptop or desktop #
    2/Enter the Bios "tap F2 or Delete " #
    3/secure Boot Must be Off ! #
    4/Fast Boot Should Be Off #
    5/UEFI With CSM (Legacy suport) #
    ###############################

    now you need to download your desired Version of Kali and burn it to dvd or usb ..

    plug it in and start your system.. tap F11 and hit UEFI Live Usb or DVD .. you should be in kali linux welcoming page..

    select the live cd or the first option And HIT "E" on your keyboard to edit the kernal parameters or options ..

    you should see line like this or similar to it ..

```
 file=/cdrom/preseed/ubuntu.seed boot=casper initrd=/casper/initrd.gz

```  after initrd.gz i have added "nomodeset and xforcevesa" and it worked like a charm ..i have two display cards in this laptop  (INtell and Nvidia ) so i picked that options and it worked !

    you can use noapic noapci nosplash irqpoll and a lot of options to fix problems like that>>

    for me nomodeset was enough coz of the Nvidia card

    goodluck guys and please if this fix worked for you please confirm it in here with your laptop type and all spec .. thx 

--------------------------------------------------------------------
UPDATE

Nvidia card + nouveau driviers was causing the problem ! by adding the option "***nomodeset***" it will let you inside the GUI of the live cd or usb BUT .. not when you finish Installing the system

so it was a headech for me trying and searching and testing for a away  to make it up and running with both intel and nvidia or just disable  the Nvidia card.. after 1 full day > the kernel option "*** modprobe.blacklist=nouveau*** " will stop the drivers and problem SOLVED !

---

### Post by MAFoElffen on 2015-12-27
Note to OP: please revisit this thread. Go up to the Threads tools link in the upper right to mark this thread as solved.

Note to Mod's: This thread could be moved to "Other Distro's"? As memory & Linux trivia reminds me, that although Kali is still similar in structure to Ubuntu, this branches predecessor (BackTrack) was derived from Ubuntu, but this derived rewrite (Kali) was based on Debian Jessie, so (as far as I know) Ubuntu is no longer the parent of this distribution. (Debian and Kali both have support forums)

---

### Post by matt_symes on 2015-12-27
@OP.

Please use the standard font size and the standard font colour. 

I have edited your post to make it readable on the myriad of devices people use to view these forums. 

Using the standard font size and colour is the best way to achieve this.

---

### Post by P0c-TeaM on 2015-12-27
> **MAFoElffen said:**
> Note to OP: please revisit this thread. Go up to the Threads tools link in the upper right to mark this thread as solved.

Note to Mod's: This thread could be moved to "Other Distro's"? As memory & Linux trivia reminds me, that although Kali is still similar in structure to Ubuntu, this branches predecessor (BackTrack) was derived from Ubuntu, but this derived rewrite (Kali) was based on Debian Jessie, so (as far as I know) Ubuntu is no longer the parent of this distribution. (Debian and Kali both have support forums)

This is not only about kali .. this also will work with ubuntu ..

You welcome ; )

---

### Post by lisati on 2015-12-27
> **P0c-TeaM said:**
> This is not only about kali .. this also will work with ubuntu ..
Which version(s)? Things have changed a lot since I started using Ubuntu back in 2007, and are likely to change again.

---

