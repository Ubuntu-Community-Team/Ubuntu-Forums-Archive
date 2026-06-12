---
title: "fglrx troubles"
date: 2007-02-17
forum: Absolute Beginner Talk
---

### Post by TekMuzik on 2007-02-17
I've been following a few guides trying to get my ATI card to work with the fglrx drivers. All of them have the same problem. After I get fglrx loaded up and my xorg.conf edited, and reboot Ubuntu, my screens no longer receive a signal. I load up Ubuntu in recovery mode and type in "fglrxinfo" and get the message "Error: Unable to open display :0". Any ideas? Thanks.  :confused:

I had it working fine on my 6.06 install, but recently bought a bigger hard drive and upgraded to 6.10.

---

### Post by Maestro23 on 2007-02-17
What is your card?  What guide are you following?

---

### Post by nickoli_02 on 2007-02-17
I had the same problem going from Dapper to Edgy. Did you include the following in your xorg.conf?

```
Section "Extensions"
           Option "Composite" "Disable"
EndSection
```

---

### Post by TekMuzik on 2007-02-17
> **Maestro23 said:**
> What is your card?  What guide are you following?

ATI Radeon 9550
and
I tired this one - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and this one - [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
I now see the second one I used says it's for 6.06 only. But both of them did the same thing.

> **nickoli_02 said:**
> I had the same problem going from Dapper to Edgy. Did you include the following in your xorg.conf?

```
Section "Extensions"
           Option "Composite" "Disable"
EndSection
```


Yes.

---

### Post by TekMuzik on 2007-02-17
P.S.   I'm doing all this to try to enable the dual monitors on Ubuntu 6.10. If anybody knows another way to do this without using fglrx, that would work just as well for me.

---

### Post by TekMuzik on 2007-02-19
*bump*
Last try. No one?

---

### Post by nickoli_02 on 2007-02-19
There is an open source ATI driver called radeon that may work with your card... see [this]("http://www.ubuntuforums.org/showthread.php?t=149997&highlight=radeon+driver+install") thread. Hope that helps!

---

### Post by TekMuzik on 2007-02-19
> **nickoli_02 said:**
> There is an open source ATI driver called radeon that may work with your card... see [this]("http://www.ubuntuforums.org/showthread.php?t=149997&highlight=radeon+driver+install") thread. Hope that helps!

But can I get dual monitors running off the Radeon driver? That ATI driver that Ubuntu has loaded on default works fine, but just provides the same image to both monitors. All the dual monitor guides I've seen used fglrx. And I had fglrx running fine on the same computer with Ubuntu 6.06. But 6.10 is giving me lots of problems (with more than just monitors.)

---

### Post by petri on 2007-02-19
> **TekMuzik said:**
> ATI Radeon 9550
and
I tired this one - [https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
and this one - [http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Dapper_Installation_Guide)
I now see the second one I used says it's for 6.06 only. But both of them did the same thing.

...

Did you know there is a guide for Edgy too? Just change Dapper to Edgy like this: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I have an 8500 and fglrx does run with Dapper but not with Edgy so guess which one I use as primary desktop :)

---

### Post by TekMuzik on 2007-02-19
> **petri said:**
> Did you know there is a guide for Edgy too? Just change Dapper to Edgy like this: [http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Edgy_Installation_Guide)

I have an 8500 and fglrx does run with Dapper but not with Edgy so guess which one I use as primary desktop :)

Opps, that's the link I was looking for. I actually used that one already. Same thing. Maybe it's a lost cause? Maybe I should just use 6.06? :(
I have no idea how the different window managers work, would using Kubuntu possibly have an effect?

---

