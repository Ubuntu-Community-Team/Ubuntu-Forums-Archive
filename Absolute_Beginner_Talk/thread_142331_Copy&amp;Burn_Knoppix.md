---
title: "Copy&amp;Burn Knoppix?"
date: 2006-03-10
forum: Absolute Beginner Talk
---

### Post by xyz on 2006-03-10
Hello,
I kind of feel stupid asking this but I just cannot figure how to make a copy of Knoppix CD which is right now in my CD-ROM?
I am currenly having trouble booting on Breezy that is why I am using Knoppix to post this. I want to make a copy of Knoppix to try to initiate a friend to GNU Linux.
So how can I make a copy of the Knoppix CD under Knoppix?

---

### Post by rboss on 2006-03-10
Well, since I don't have Knoppix installed and don't know about the tool it provides, I just give you the most basic variant:

cat /dev/cdrom > knoppix.iso

This way you can create an iso of the cdrom.

To burn the thing, just use a iso-aware cd burn program. Use cdrecord, for example.

---

### Post by xyz on 2006-03-10
Sorry...I think I was not clear enough in my previous post.
I am right now using the Live Knoppix CD of which I want to make a copy.
How do I, so to speak, transfer what is on that Live CD, for instance, to my desktop so that I can burn a new Live CD?
Thank you.

---

### Post by LordBug on 2006-03-10
If you're booting the Knoppix CD and asking how to then copy it, I would suggest talking to Knoppix on how, or booting to your primary OS and doing it from there.

In Ubuntu, Gnomebaker and K3B should be able to handle it.

---

### Post by taurus on 2006-03-10
Wouldn't it be much easier and simpler if you just download the iso again for Knoppix?  Then, burn it onto a CD and give that to your friend...

---

### Post by xyz on 2006-03-10
[QUOTE=taurus]Wouldn't it be much easier and simpler if you just download the iso again for Knoppix?  Then, burn it onto a CD and give that to your friend...[/QUOTE]
Yes Sir...that is what I am doing right now. Once in a while, I wonder if I have got any grey cells left.
Thanks.
But technically I still wonder if it is possible...
Sorry to have taken up space and time for no valid reason.

---

### Post by taurus on 2006-03-10
Yes, it is possible to master the content of a CD and convert it to an iso but since there is already one available for you to download, then always take the easy road!!!

---

