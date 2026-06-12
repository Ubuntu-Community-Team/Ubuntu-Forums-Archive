---
title: "Asus X401A-BHPDN41"
date: 2012-11-23
forum: Asus Ubuntu Support (CLOSED)
---

### Post by caffeinatedev on 2012-11-23
Has anyone had luck with running Ubuntu with the Asus X401A-BHPDN41 notebook? 

Specs:

Intel Pentium CPU B980 @ 2.40GHz
4.00GB RAM
x64-based processor

Current Operating System:

Windows 8 64-bit

---

### Post by 2F4U on 2012-11-23
Can you be more specific? What are your problems?

---

### Post by caffeinatedev on 2012-11-24
Specifically, I can't access BIOS from the boot screen and so I can't boot from USB.

Installing Ubuntu via Wubi presents some sort of error on boot up which basically won't allow me to boot into anything other than Windows.

Note that this is not ARM architecture so the user *should* be able to disable Secure Boot. My problem is that I don't know how to disable Secure Boot or even how to check to see if Secure Boot is enabled.

**The hardware doesn't seem to be the issue because I successfully ran Ubuntu in a VM.

---

### Post by 2F4U on 2012-11-24
> Specifically, I can't access BIOS from the boot screen and so I can't boot from USB.

There is usually a particular key you should press to get into the BIOS. Unfortunately, this is vendor specific, but often pressing F1 or F2 gets you in the BIOS. On some machines you can temporarily change the boot order by pressing F11 or F12 (depends on the machine) while the BIOS screen is active.

> Installing Ubuntu via Wubi presents some sort of error on boot up which  basically won't allow me to boot into anything other than Windows.

You would have to be more specific in what the error message is.

> Note that this is not ARM architecture so the user *should* be able to  disable Secure Boot. My problem is that I don't know how to disable  Secure Boot or even how to check to see if Secure Boot is enabled.

To be honest, you can't attribute this Secure Boot thing to Ubuntu since it is clearly a Microsoft "invention".

> **The hardware doesn't seem to be the issue because I successfully ran Ubuntu in a VM.

Totally irrelevant. The VM present the OS (Ubuntu) with a generic hardware designed by the VM vendor. It really has nothing to do with your real hardware and running any Linux distribution in a VM tells you nothing about how it runs on your real hardware. This is the whole purpose of virtualization, to be independent from particular hardware.

---

### Post by sigmatht on 2012-11-24
> **caffeinatedev said:**
> Specifically, I can't access BIOS from the boot screen and so I can't boot from USB.

Installing Ubuntu via Wubi presents some sort of error on boot up which basically won't allow me to boot into anything other than Windows.

Note that this is not ARM architecture so the user *should* be able to disable Secure Boot. My problem is that I don't know how to disable Secure Boot or even how to check to see if Secure Boot is enabled.

**The hardware doesn't seem to be the issue because I successfully ran Ubuntu in a VM.

Power off your machine, turn it on and hit f2.  I like to just keep hitting it repeatedly until bios comes up.

Source: [http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X401A&s=415&hashedid=xExBKNBOtGWUPlvR&os=8&no=1028](http://support.asus.com/Troubleshooting/detail.aspx?SLanguage=en&p=3&m=X401A&s=415&hashedid=xExBKNBOtGWUPlvR&os=8&no=1028)

---

### Post by bg4545 on 2012-11-25
I've got the same laptop in green. The issue with not being able to access the BIOS settings or boot a USB is because of Windows 8. Windows 8 skips the Boot options. In order to change settings you have to boot Windows and go to the PC Settings and under "General" if you scroll down it  "Advanced Startup". You can click Restart now to load the Boot Menu and you can change BIOS settings there or Boot from a USB drive.
I haven't had any luck loading Ubuntu though, it just loads to a Black screen. I used Universal USB Installer to create the USB.

---

### Post by caffeinatedev on 2012-11-25
I feel like a n00b for not knowing about the VM thing, which I guess I still am :lolflag:

All very useful advice guys, thank you very much. I was able to access BIOS using F2 but the options available are very confusing to me.

I take it that the black screen is for a lack of a video driver?

And I'll be sure to post the error message when I get a chance to attempt a Wubi install again.

---

### Post by GaryTheCat on 2012-11-26
I'm hoping to buy one of these with Win7 preinstalled - I'm not too bothered about dual booting with Windows but may consider it.

Does anyone think I'll have the problems mentioned above?

Many thanks

G

---

### Post by caffeinatedev on 2012-11-27
> **bg4545 said:**
> I've got the same laptop in green. The issue with not being able to access the BIOS settings or boot a USB is because of Windows 8. Windows 8 skips the Boot options. In order to change settings you have to boot Windows and go to the PC Settings and under "General" if you scroll down it  "Advanced Startup". You can click Restart now to load the Boot Menu and you can change BIOS settings there or Boot from a USB drive.
I haven't had any luck loading Ubuntu though, it just loads to a Black screen. I used Universal USB Installer to create the USB.

I can't figure out how to boot from USB. How did you do it?

---

### Post by caffeinatedev on 2012-11-27
> **GaryTheCat said:**
> I'm hoping to buy one of these with Win7 preinstalled - I'm not too bothered about dual booting with Windows but may consider it.

Does anyone think I'll have the problems mentioned above?

Many thanks

G

If it's the same hardware, most definitely. But Secure Boot shouldn't be a problem for you.

---

### Post by caffeinatedev on 2012-11-27
I did it and here's how it was done:

[LIST]
[*]I disabled Secure Boot in the BIOS by pressing F2 at boot.
[*]Pressing ESC at boot presents a boot menu where you can choose to boot from USB.
[*]I ran an Ubuntu x64 live USB and Ubuntu finished installing before I could even finish the first act of Hamelt!
[/LIST]
The Pros:

[LIST]
[*]Ubuntu boots and runs very fast, faster than Windows 8, even.
[*]Everything seems to be compatible without proprietary drivers (there are none available for Ubuntu)
[/LIST]
The Cons:

[LIST]
[*]function keys do not work (do I need to file a bug report for this?)
[/LIST]

---

### Post by Pendertuga on 2012-11-27
> **caffeinatedev said:**
> I did it and here's how it was done:

[LIST]
[*]I disabled Secure Boot in the BIOS by pressing F2 at boot.
[*]Pressing ESC at boot presents a boot menu where you can choose to from USB.
[*]I ran an Ubuntu x64 live USB and Ubuntu finished installing before I could even finish the first act of Hamelt!
[/LIST]
The Pros:

[LIST]
[*]Ubuntu boots and runs very fast, faster than Windows 8, even.
[*]Everything seems to be compatible without proprietary drivers
[/LIST]
The Cons:

[LIST]
[*]function keys do not work (do I need to file a bug report for this?)
[/LIST]



[LIST]
[/LIST]

Do you mean the F keys or the Fn + keys? I'm also using this laptop and if you're talking about the Fn + F5 - F7 to change the brightness then I feel your pain. All the other ones seem to work for me though.

---

### Post by bg4545 on 2012-11-28
The issue I had with the black screen was because of the Secure Boot option. After completely disabling it I am able to run Ubuntu.
The booting issue I mentioned before was that, since my BIOS was set to Fast Boot, I could not press any boot options on start up (F2 or Esc do nothing, Windows 8 starts anyways). The way to change options and boot from other drives is through the Windows 8 PC Settings. Disabling Fast boot in my BIOS allowed me to enter the boot options you described on start up.
Testing it out right now it seems brightness down (fn + f5) and brightness up (fn+f6) are the only ones that do not work, all other hot keys work.

---

### Post by caffeinatedev on 2012-11-28
> **Pendertuga said:**
> Do you mean the F keys or the Fn + keys? I'm also using this laptop and if you're talking about the Fn + F5 - F7 to change the brightness then I feel your pain. All the other ones seem to work for me though.

I was talking about the Fn keys but it seems that the brightness keys ARE the only ones effected.  My question is what route do we take with the non-functioning brightness keys and how do we repair the Windows 8 install? Believe it or not, keeping a legitimate version of Windows is appealing to me.

In other news, I'm elated to be reunited with Tux <3

---

