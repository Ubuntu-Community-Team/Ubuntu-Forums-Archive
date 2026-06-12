---
title: "automatix decision"
date: 2007-05-09
forum: Absolute Beginner Talk
---

### Post by em11488 on 2007-05-09
I started automatix 2 and it says 
automatix will unmount all of your existing fat32 and ntfs  partitions and remount them as writable partitions. if you want automatix to continue, then hit yes or else hit no. if you hit no, automatix will ignore this option.

if i hit yes will it mess up my system? should I hit yes or no.?

---

### Post by Nythain on 2007-05-09
theoretically no it wont mess anything up... possibly, yes, then again, possibly just mentioning the word automatix can summon forth a mysterious lightening bold you cant see to nuke your entire system...

---

### Post by em11488 on 2007-05-09
what would you do though, do you put your faith in the program

---

### Post by Shazaam on 2007-05-09
Automatix shouldn't ask you a question like that unless you added a program from the Automatix list for installation such as ntfs-3g. If you dont feel comfortable doing that just click cancel or no.
I have used Automatix before and I haven't had any problems with it.

---

### Post by ramjet_1953 on 2007-05-09
I have used Automatix in Dapper, Edgy and Feisty and have never had a problem
Why? Because it is easy and saves me some time.

Probably the best advice I can give is DO NOT try to stop a script when it is running. That seems to be the main problem that people have. Some packages, like the codecs and fonts take a while to download.

Don't forget that disasters can happen with any system and any download. You only need to visit these forums to realise that things can go horribly wrong, just using Add/Remove and Synaptic.

On balance, I don't think that Automatix is any more dangerous to use than Synaptic or the command line sudo apt-get install commmand.

Regards,
Roger :cool:

---

### Post by la3875 on 2007-05-09
You make the call... If you have sensitive data and other users of that data, do as I did and choose no. You can always mount it manually as read only if you want to get at files for use in Ubuntu.

---

### Post by Nythain on 2007-05-09
would i trust it personally, sure.

---

### Post by Saphira on 2007-05-10
Automatix is known for breaking systems and you'll find that you really don't need it.

---

### Post by mstlyevil on 2007-05-10
> **em11488 said:**
> I started automatix 2 and it says 
automatix will unmount all of your existing fat32 and ntfs  partitions and remount them as writable partitions. if you want automatix to continue, then hit yes or else hit no. if you hit no, automatix will ignore this option.

if i hit yes will it mess up my system? should I hit yes or no.?

That is a message for installing NTFS-3g. Automatix makes a date time based backup of the fstab file before making any changes. If you are uncomfortable with this just select no. Very few problems have been reported using this function.

If you need support for Automatix related issues please come to [the Automatix Support Forum.]("http://www.getautomatix.com/forum/")

---

### Post by Pobega on 2007-05-10
[QUOTE=ramjet_1953;2620095On balance, I don't think that Automatix is any more dangerous to use than Synaptic or the command line sudo apt-get install commmand.[/QUOTE]

So dpkg --force-all is safe? Because if memory serves me right that's how Automatix unpacks it's .deb files. I could be wrong though, but if it is true I wouldn't recommend touching Automatix with a ten foot pole. --force-all is only useful if one knows what they're doing, but forcing debs to unpack in an automated environment is a horrible practice.

---

### Post by mstlyevil on 2007-05-10
> **Pobega said:**
> So dpkg --force-all is safe? Because if memory serves me right that's how Automatix unpacks it's .deb files. I could be wrong though, but if it is true I wouldn't recommend touching Automatix with a ten foot pole. --force-all is only useful if one knows what they're doing, but forcing debs to unpack in an automated environment is a horrible practice.

You are entirely wrong. Automatix does not use --force anything.

---

### Post by shuttleworthwannabe on 2007-05-10
Just out of curiosity, why are we flaming automatix here?; mstlyevil's pointer to visit the automatix forum is what the poster needed.

---

### Post by compiledkernel on 2007-05-10
Let us refrain from constant bickering over the use of automatix or not. 

If there is an Automatix issue head on over to [http://www.getautomatix.com](http://www.getautomatix.com) and get the issue fixed. 

This thread has gone way off topic from the original poster's question about support.

---

