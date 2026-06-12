---
title: "Question on sercurity and web browsing?"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by keyboardMan on 2007-06-26
Hi

I am completely new to Linux and I have finally found a distribution that is working fine with my Nvidia card, which is Ubuntu 64Bit. I have two questions about Ubuntu.....

Firstly, I understand that I am unlikely to become infected with a Virus that can harm Linux. My Ubuntu is a dual boot with Windows, but is it possible to download a Windows Virus in Linux then for it somehow to pass into my Windows partition? Ubuntu can see my Windows partition, but I don't think I can edit any files on it etc. I am just worried that Malware could pass through the back door so to speak.

Second question:
I like Youtube and I noticed the Videos would not play, so I download Gnash flash player from the Synaptic package browser with the Mozilla plugins. When I go to view a video I just see a the play, stop etc bar flashing in the center and no sound or Video?

I hope someone can help:)
Regards

---

### Post by mikewhatever on 2007-06-26
Welcome to the forums.
You may want to read the following about security. [http://psychocats.net/ubuntu/security](http://psychocats.net/ubuntu/security)

---

### Post by Seisen on 2007-06-26
Gnash is the gnu version of flash. There are ways to get flash installed on a 64-bit computer.

[http://ubuntuforums.org/showthread.php?t=341727]("http://ubuntuforums.org/showthread.php?t=341727")

---

### Post by FleetAdmiral74 on 2007-06-26
Unless you have installed ntfs write access, I don't think malware could move onto the other partition. Just don't be stupid and you won't get it in the first place...

Firefox + AdBlock Plus + NoScript = No malware for me

---

### Post by trak87 on 2007-06-26
> **keyboardMan said:**
> ...is it possible to download a Windows Virus in Linux then for it somehow to pass into my Windows partition? Ubuntu can see my Windows partition, but I don't think I can edit any files on it etc. I am just worried that Malware could pass through the back door so to speak.

It's entirely possible.

---

### Post by keyboardMan on 2007-06-26
Thanks for the replies 

I have just installed Ad-block +  Noscript and it's nice not to see them annoying ads no more :)

So a long as I don't permit write access to my Windows partition I should be ok? I tried moving a file to the windows partition and I was informed that I didn't have access, so gather that also means Malware couldn't write to the driver either.

---

### Post by tgbrowning on 2007-06-26
Just looked at trying to copy a file, using sudo, in the windows partition into a second, new file of the same folder and got the following message:

cp: cannot create regular file `temppw.txt.copy': Read-only file system

Which is more or less what I expected. 

Unless the malware gets in and aquires something even higher than superuser status, I can't see how it could move to a read-only partition. 

Browning>>>

---

### Post by trak87 on 2007-06-26
> So a long as I don't permit write access to my Windows partition I should be ok?

We can make our systems safer, but not totally safe. The operating system architecture is one key factor to computer security and that's why I prefer Linux over MS, although in the final analysis these are still only consumer operating systems.

---

### Post by keyboardMan on 2007-06-26
If it was practical I would move to Linux permanently and ditch Windows, but I play many 3D games that require windows. 

What I like about Linux
.Its free (obvious I know)
.Feels more responsive 
.Saves Money because it can run on older hardware because take MS Vista for example its bloatware and even the most upto date systems run it sluggish.
.No need for expensive Anti-virus solutions
.Loads of free software avaliable 

Microsoft claim that Vista is very secure, but they claim this for every edition and every time it turns out not to be the case. It's kind of amusing that a multi billion dollar company can't get it right lol

---

### Post by eldepeche on 2007-06-26
> **keyboardMan said:**
> 
I like Youtube and I noticed the Videos would not play, so I download Gnash flash player from the Synaptic package browser with the Mozilla plugins. When I go to view a video I just see a the play, stop etc bar flashing in the center and no sound or Video?
Gnash only supports Flash features up to version 6 or 7, and it won't play any flash videos that I know of. 

If you run the 32-bit version of Firefox (or any other flash-capable browser), then you can use the Adobe/Macromedia version. Check out [this link](https://help.ubuntu.com/community/FirefoxAMD64FlashJava).

---

