---
title: "Care and attention."
date: 2006-04-17
forum: Absolute Beginner Talk
---

### Post by Michiba on 2006-04-17
Hi All,

As an ex Windows user, I am used to maintaining my computer system.

I would daily,

Run a virus checker
Run a Malware checker

Weekly delete my internet Cache and all cookies
Weekly do a disk clean up
Weekly defrag my hard drive

What should I do with Ubuntu to maintain a clean and efficient system? 

Any recomendations on Virus checkers and Malware checkers appreciated.

Thanks as always

Michiba

---

### Post by Sutekh on 2006-04-17
Well you can now look forward to a holiday!

Probably the most important thing is to ensure that you have the latest upgrades from the supported Ubuntu repositories.
```
sudo apt-get update
sudo apt-get upgrade
```
Or use the "Reload" and "Mark All Upgrade" buttons in Syanptic.

If you are really worried, then you could look into install an antivirus program, [Clam AV](http://www.clamav.net/), to catch the very few Linux virus floating around.  I don't even know if there is MalWare software for Linux.

Other than that you have no need to 'disc clean up' or 'defrag'.

---

### Post by Borniet on 2006-04-17
Just use it...
There is no real treath of virusses on Linux, so no virusscanner needed.
Malware, same issue.
Delete your internetcache and cookies: depends on which browser you use, in Firefox you can do it using the settings I believe.
Disk cleanup: If you've installed some new programs using apt-get, you can do a 'sudo apt-get autoclean' to delete the packages that are installed and no longer needed.
Disk defrag: not needed when you are using the ext2 or ext3 filesystem, as they don't clutter up like FAT.

Hope this helps!

---

### Post by rfruth on 2006-04-17
You're a very attentive user Michiba, welcome to Linux land where malware doesn't roam 8) clamAV and a firewall is a good idea ...

---

### Post by jorn on 2006-04-17
Ubuntu hasn't got any viruses yet as far as I know.
No defrag is needed. The disk is checked every 30 bootup.
Cache and cookies you can remove in your browswer.
Ther is a virusscanner for Linux, I don't know the name.

Jorn

---

### Post by Michiba on 2006-04-17
Hey,

Thanks for the reply, surely it can't be that simple or I would have changed to Linux years ago???

What happens to all those malicious cookies from the internet?

All sounds so easy, is LInux that efficient and self regulating?

If it is, I'm happy and won't complain

Thanks
Michiba

---

### Post by nanotube on 2006-04-17
sutekh and borniet give good advice.
for more discussion on the necessity of firewall and/or antivirus on linux, see this thread:
[http://ubuntuforums.org/showthread.php?t=131616](http://ubuntuforums.org/showthread.php?t=131616)

imho, 
-antivir is quite unnecessary, 
-firewall is nice to have but i suppose not really necessary if you are not planning on running any sort of services at all (but you can check link in my sig and go to firewall section to see how to set up a simple but robust ruleset)
-defrag is unnecessary if you are running on the default ext3 filesystem
-sudo apt-get autoclean (as posted above) is just about the only thing you need to "clean" your disk
-removing cache and cookies is still a decent idea ;)

---

### Post by Borniet on 2006-04-17
[QUOTE=Michiba]Hey,

Thanks for the reply, surely it can't be that simple or I would have changed to Linux years ago???

What happens to all those malicious cookies from the internet?

All sounds so easy, is LInux that efficient and self regulating?

If it is, I'm happy and won't complain

Thanks
Michiba[/QUOTE]
One word: YUP  ;)

---

### Post by Michiba on 2006-04-17
To all,

Thanks again, I have seen the light unfiltered through Windows and I like it. I will feel much more comfortable with an AV package and will look into it. 

Other than that my conversion is complete.

Thanks agian

Michiba

---

### Post by nalmeth on 2006-04-17
If you'd really like, look into Avast Antivirus, recently ported to linux. You can use it to scan a windows partition, or possibly your email's to prevent you from passing them on to other's.

---

### Post by Michiba on 2006-04-17
Thanks Nalmet,

I no longer have a windows partition on my machine.

Very appreciative

Michiba

---

