---
title: "ubuntu from cd"
date: 2005-12-10
forum: Absolute Beginner Talk
---

### Post by jtmedin on 2005-12-10
Read the article from pc world about running ubuntu from cd. Downloaded the .iso file & used nero to make a bootable cd with that file. Booted the pc & got a dr dos startup. Ended with an A: prompt. Tried all kinds of commands no banana. What am i missing? TIA

---

### Post by Estariel on 2005-12-10
Are you sure you booted from the CD? (and not from a DOS floppy for example?)

There is definately no DOS present on the Ubuntu CD.

---

### Post by Qrk on 2005-12-10
Do you mean the Live CD? Looks like you burned it right... but it must not be booting.

You need to change your boot order. When your computer first starts up, it should say something like "Press X to enter setup" before any OS is loaded.

The key you must press varies per manufacturer. It is probably Delete, Esc or F12.  Be sure to check your manufacturer's website for the exact key. 

Once in the BIOS (setup), make the CD drive the first thing the computer trys to boot to, then the hardrive.

---

### Post by linbetwin on 2005-12-10
If the boot order weren't correct, the machine would have booted to Windows.

---

### Post by Qrk on 2005-12-10
Didn't it? Why else would there be a Dos prompt labled A:  ? That doesn't sound like Linux.

---

### Post by linear on 2005-12-10
I've read elsewhere that dr dos is put there by Nero, and it's a sign that you didn't have the correct settings in Nero when you burned the CD.

See this link for Nero instructions:

[http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487](http://help.ubuntu.com/starterguide/C/faqguide-all.html#id2455487)

---

### Post by xmastree on 2005-12-11
A very common mistake. What you've done is told Nero to make a bootable CD containing the ISO. Nero has a built in boot image, which is what you booted into.

[www.xmastree.34sp.com/ubuntu/burn](www.xmastree.34sp.com/ubuntu/burn)

That shows you step by step how to do it correctly.

---

### Post by jtmedin on 2005-12-13
Ok you have it correct i told nero to make a bootable cd. Will try again this week-end.

---

### Post by jtmedin on 2005-12-13
Fine i am online. Wonder how the network dsl got by the wep security?

---

### Post by HarrisonHopkins on 2006-06-20
Sorry if we aren't allowed to bring up old threads, but I am having this same problem.

I didn't use Nero though. I used CDBurnerXP Pro 3. Anyone have any instructions for that? I did exactly as the instructions for burning an .iso said.    

1.

      Verify the ISO file. [WWW] Instructions on OpenOffice.org.
   2.

      Download and install [WWW] an ISO burner.
   3.

      Launch the ISO burner > File menu > Write disk from ISO file > select the ISO file. (Make sure you set the cd as bootable so it starts up from there at bootup.)

---

### Post by FredB on 2006-06-20
Maybe this could help :

[http://cdburnerxp.se/help/english/burniso]("http://cdburnerxp.se/help/english/burniso")

---

