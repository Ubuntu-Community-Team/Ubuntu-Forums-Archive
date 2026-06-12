---
title: "MACUNTU 12.04 BETA made for latest gen macbooks"
date: 2012-10-01
forum: Apple Hardware Users
---

### Post by nerdkiller14 on 2012-10-01
Hello,

I have just made a custom distro called MACUNTU. It is in the Beta phase. It uses either Unity or Cinnamon for GUI.  It works with the retina macbook pros and should work with last and latest gen macbook pros. I need some testers so if you are interested reply to this post. 

Wifi and Graphics work out of the box!!!

---

### Post by raymo03 on 2012-10-02
I'd be interested in helping to test. I was disappointed my rMBP has issues with linux.

---

### Post by bigcfk on 2012-10-02
I'd be interested to help test this too! 
Though the name ma****u is a little edgy, no?

---

### Post by nerdkiller14 on 2012-10-03
If you would like to sugest a name that would be fine just comment. I made it up just for this post. 
I ran updates and broke GPU drivers I fix it soon. but in the meantime anyone know where I can host the ISO when I am done?

---

### Post by nerdkiller14 on 2012-10-03
> **bigcfk said:**
> I'd be interested to help test this too! 
Though the name ma****u is a little edgy, no?

Oh! never noticed that sorry any suggestions are welcome!

macintu?

---

### Post by mijxyphoid on 2012-10-05
I am definitely interested in this release !!!!!
Please post up more information on how and where we can try this !:p

(I kinda like the name MACUNTU, considering how much pain it is to get Ubuntu working on this $2.5K aluminium door stop).

I originally bought this thing because I wanted something future proof to develop iOS apps, and run Linux 90% of the time....

Sadly I have gotten no-where on the linux side of things, and I now carry two laptops around to satisfy my Linux and iOS development needs.

---

### Post by mick463 on 2012-10-05
> **nerdkiller14 said:**
> Hello,

I have just made a custom distro called MACUNTU. It is in the Beta phase. It uses either Unity or Cinnamon for GUI.  It works with the retina macbook pros and should work with last and latest gen macbook pros. I need some testers so if you are interested reply to this post. 

Wifi and Graphics work out of the box!!!

I will give it a go where do i get the iso

---

### Post by JungleJoker on 2012-10-05
I just started IT in college and need to install linux. So far I haven't found any distro that would install natively on my MacBook Pro 9,1. Even though this is in beta development, I would love to give it a go!

---

### Post by nerdkiller14 on 2012-10-07
> **JungleJoker said:**
> I just started IT in college and need to install linux. So far I haven't found any distro that would install natively on my MacBook Pro 9,1. Even though this is in beta development, I would love to give it a go!

I am currently having troubles with display drivers 

[https://docs.google.com/open?id=0B9KmZX8A6stJNDRhZUR2TVRyVXM](https://docs.google.com/open?id=0B9KmZX8A6stJNDRhZUR2TVRyVXM)

^
|
Link to iso

To boot edit grub boot up parameters and add without quotes

" noapic nopci nomodeset nointremap"

When booted it will give you a prompt type "startx".

Please try and tell me if it works for you. You must burn to USB stick using "UNETBOOTIN" (google it). Then restart computer while holding down "ALT(option)"

You will see 2 new partitons "orange in color" select the non EFI one.  

When in grub menu highlight "Try as .........." and then press "TAB"

This will open the grub menu delete the "--" and start type parameters given above.

---

### Post by will1982 on 2012-10-07
Sounds cool, but the name...
In between the ma and u.. xD

---

### Post by nerdkiller14 on 2012-10-07
> **will1982 said:**
> Sounds cool, but the name...
In between the ma and u.. xD


I'm open for suggestions.

---

### Post by will1982 on 2012-10-07
Maybe Macbuntu?
That seems like how the other Ubuntu spin-offs were named

---

### Post by qqldd on 2012-10-14
> **nerdkiller14 said:**
> I am currently having troubles with display drivers 

[https://docs.google.com/open?id=0B9KmZX8A6stJNDRhZUR2TVRyVXM](https://docs.google.com/open?id=0B9KmZX8A6stJNDRhZUR2TVRyVXM)

^
|
Link to iso

To boot edit grub boot up parameters and add without quotes

" noapic nopci nomodeset nointremap"

When booted it will give you a prompt type "startx".

Please try and tell me if it works for you. You must burn to USB stick using "UNETBOOTIN" (google it). Then restart computer while holding down "ALT(option)"

You will see 2 new partitons "orange in color" select the non EFI one.  

When in grub menu highlight "Try as .........." and then press "TAB"

This will open the grub menu delete the "--" and start type parameters given above.

Yes! It worked! I will explore more

---

### Post by nerdkiller14 on 2012-10-16
Working on getting NVIDIA drivers on it should be done by this weekend. I am having problems with the mouse not showing up any ideas?

---

### Post by nerdkiller14 on 2012-10-17
> **will1982 said:**
> Maybe Macbuntu?
That seems like how the other Ubuntu spin-offs were named

Name will be change in next BETA.
Working on NVIDIA drivers can't get mouse to appear.

---

### Post by nerdkiller14 on 2012-10-18
Hey guys is it ok if I change from ubuntu to linux mint which is based on Ubuntu.

---

### Post by rg4w on 2012-10-18
> **will1982 said:**
> Maybe Macbuntu?
That seems like how the other Ubuntu spin-offs were named
I believe the "*buntu names are governed under trademark license from Canonical.  And since "Mac" is a registered trademark of Apple, both sides of that name seem risky.

---

### Post by nerdkiller14 on 2012-10-18
> **rg4w said:**
> I believe the "*buntu names are governed under trademark license from Canonical.  And since "Mac" is a registered trademark of Apple, both sides of that name seem risky.

Would it be ok if i switch it over to linux mint and call it iMint?

---

### Post by rg4w on 2012-10-18
> **nerdkiller14 said:**
> Would it be ok if i switch it over to linux mint and call it iMint?
I believe Apple was awarded a patent on the letter "i".

Darn!  I just used "i" - I need to pay them royalties.

Darn!  Just used it some more!  I guess I can expect to be hauled into court soon... ;)

---

### Post by nerdkiller14 on 2012-10-18
anybody can help me I am now getting the error 
intranmfs no bootable medium found.

---

### Post by nerdkiller14 on 2012-10-22
> **nerdkiller14 said:**
> anybody can help me I am now getting the error 
intranmfs no bootable medium found.

Almost fully working!!!! Once this gets about of beta can any please help by donating so I can host a website.  I am hoping to get this to be a live cd for all macs that are produced. Thanks again. 

NOTES:
It is based on 12.04.1 (most drivers needed on mac are not compatible with kernel 3.5.

---

### Post by ksatta1 on 2012-12-23
I've been tweaking Ubuntu on my Macbook Pro 15" Retina now for a few days. Have you really gotten the wireless to work perfectly? The only major problem I have is the wireless disconnecting, not connecting, packet loss, etc.. It seems to be a power management issue (if I manually drop the txpower then it works a bit better for a while etc).

You can drop the txpower with:
```
sudo iwconfig wlan0 txpower <number>
```
(3 seems to work a bit better for me, by default it just uses 20 all the time)

Right now I'm running 12.10 according to the instructions here: [http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/](http://cberner.com/2012/10/19/installing-ubuntu-12-10-on-macbook-pro-retina/)

Also tried ndiswrapper with the BootCamp drivers, but they didn't work.

---

