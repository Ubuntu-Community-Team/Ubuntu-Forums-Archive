---
title: "How to make a ubuntu live usb bootable on a Mac in Ubuntu?"
date: 2017-04-20
forum: Apple Hardware Users
---

### Post by monkeybrain20122 on 2017-04-20
Hi, I would like to make a live Ubuntu usb for my friend. But it turns out that live Linux usbs created with the usual ways don't work on Mac (I never had a Mac so didn't know that) From google you need to use something called Mac Linux usb loader but it seems that it is a Mac application. Is there a way to make a live usb bootable on a Mac using only tools that can be run on Ubuntu?

Thanks.

---

### Post by RobGoss on 2017-04-20
Hello and welcome to the forum, I'm like you don't know to much about Macs, but I did find this tutorial that might help you get started [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos)

---

### Post by &amp;KyT$0P# on 2017-04-20
Is [rEFInd]("http://www.rodsbooks.com/refind/") installed on this Mac?

---

### Post by howefield on 2017-04-21
Thread moved to the "*Apple Hardware Users*" forum for a better fit.

---

### Post by monkeybrain20122 on 2017-04-21
> **RobGoss said:**
> Hello and welcome to the forum, I'm like you don't know to much about Macs, but I did find this tutorial that might help you get started [https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos](https://www.ubuntu.com/download/desktop/create-a-usb-stick-on-macos)

Hi, thanks for the reply. But I think that thread is about creating a ubuntu live usb on a Mac. It uses a version of unetbootin for Mac which I think is different.

---

### Post by monkeybrain20122 on 2017-04-21
> **halogen2 said:**
> Is [rEFInd]("http://www.rodsbooks.com/refind/") installed on this Mac?

Doubt that.

---

### Post by &amp;KyT$0P# on 2017-04-21
> **monkeybrain20122 said:**
> Doubt that.
That's likely the problem.  Can you install rEFInd on this Mac?

As for creating the live USB using Ubuntu, [FONT=Courier New]dd[/FONT] worked for my Mac.  But keep in mind that my Mac has rEFInd installed.

---

### Post by monkeybrain20122 on 2017-04-22
> **halogen2 said:**
> That's likely the problem.  Can you install rEFInd on this Mac?

As for creating the live USB using Ubuntu, [FONT=Courier New]dd[/FONT] worked for my Mac.  But keep in mind that my Mac has rEFInd installed.

Probably. But if i have access to the mac I would be able to create a live usb bootable from it. It did that before.

---

### Post by &amp;KyT$0P# on 2017-04-22
Hmm.  Well, if the live USB will be Ubuntu **16.04**, it might be enough just to boot rEFInd once, just to load the live USB.  After I installed 16.04, my Mac booted straight to GRUB, ignoring the installed rEFInd.

It's possible to make a [bootable USB of rEFInd]("http://www.rodsbooks.com/refind/getting.html").  If the pre-made flash drive image doesn't work, see the "Tip" to the right on that page.  And I suggest using GUID partition table if you do your own rEFInd flash drive image - I think Macs require all bootable disks to have either GUID or Apple partition table.

So maybe your friend could try booting a rEFInd USB, then from there booting the Ubuntu live USB?

(I have no experience with booting rEFInd from external media, so no idea if this would work.)

---

### Post by gsahli on 2017-04-25
AFAIK, USB drives made with Unetbootin work just fine on Intel Macs. You startup and hold the Option(Alt) key until you get the Icon Menu (boot choices). If this doesn't work, maybe that's a powerpc Mac (old).

---

