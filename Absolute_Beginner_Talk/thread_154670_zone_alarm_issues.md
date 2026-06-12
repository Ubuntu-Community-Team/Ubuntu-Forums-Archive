---
title: "zone alarm issues"
date: 2006-04-03
forum: Absolute Beginner Talk
---

### Post by darkbane on 2006-04-03
I'm relatively new to Ubuntu, but I've managed to get a lot of things working thanx to this forum.  You guys rock.

My problem is this.  I have my main XP system with a wireless connection for the internet.  I have my XP box networked with my linux box through a switch.  I've managed to get the internet onto the linux box though my main XP box.  I can only get the internet and network connections working if I disable Zone Alarm firewall on my XP box.    

I don't want to continue using the internet on XP without the firewall.  What do I need to do so that I can run Zone Alarm but still have the network operational?

I'd appreciate any comments or suggestions.  Thanx

DB

---

### Post by goatflyer on 2006-04-03
You need to be sure your home network is in your Trusted Zone.

Add the IP Address range containing your home network to the Trusted Zone in ZA

---

### Post by r4ik on 2006-04-03
Any comment ?

Switch the boxes.

Good luck.

---

### Post by darkbane on 2006-04-03
I tried that, but I wasn't positive what my IP was on my Linux box.  How do I find out what my IP range is?

What did you mean by switch the boxes?  Have the Linux box providing the Internet Feed?  I don't think I'd want to do that, since XP is still my primary Box.  I made this Linux box mainly as a testing ground to see what Linux has to offer.

---

### Post by r4ik on 2006-04-03
[QUOTE=darkbane]I tried that, but I wasn't positive what my IP was on my Linux box.  How do I find out what my IP range is?

What did you mean by switch the boxes?  Have the Linux box providing the Internet Feed?  I don't think I'd want to do that, since XP is still my primary Box.  I made this Linux box mainly as a testing ground to see what Linux has to offer.[/QUOTE]

That is exactly what i mean.
You could still use the XP box primary but i dont know if you have to change a lot at your workspace.

---

### Post by Xiunix on 2006-04-03
In the ZA Internet/Trusted Zone, you need to go to one of the tabs (I can't remember which one) and set it as an all-accepted internet in your trust zone.

Your IP Range is all but the last router section...

192.168.0.14  <----------Computer's IP ADDRESS
192.168.0  <-------------Netowork Identity (Includes all numbers after the .)

---

### Post by darkbane on 2006-04-03
OK....I think that worked, but now I'm having more network issues.

From Ubuntu I can access my shared folders on XP, but from XP, I can't seem to find the Linux Box.  Any Suggestions?  I've set up a shared folder with Samba, and it's on the same workgroup name?  

Any suggestions?

Thanx for all the other quick replies.  That's awesome

---

### Post by Xiunix on 2006-04-04
Ok then, first off, what if the format of the area where the shared folder is. Windows cannot read the native Linux format. It has to be a FAT32 (and Linux cannot read Windows' NTFS format either).

(Breezy Badger Setup)
If that's all clear, then you'll have to go to System > Prefrences > Remote Connection; and make sure the sharing boxes are selected

If that does not work you'll have to set p a direct SDH (right?) connection between the two FAT32 areas. I can't fnd the menu right now but I will shortly...if it need be.

---

### Post by xenmax on 2006-04-04
> (and Linux cannot read Windows' NTFS format either).
No offence, but i think you mean "linux can read NTFS, but cannot reliably write to NTFS yet"?

---

### Post by Xiunix on 2006-04-06
my bad, I typoed. I know that linux can READ it but writing to it is a lot to ask...it takes forever...

---

