---
title: "Hard drive crash!"
date: 2008-04-14
forum: Absolute Beginner Talk
---

### Post by silkworm_worm on 2008-04-14
Hi everyone! I installed Ubuntu a couple of months ago and my computer has been working great except for some random freezes and grinding sounds that have made me fear an impending hard drive crash. Sure enough,  last night my computer froze up again and when I tried to reboot I get a "kernel panic" error halfway through the startup process. I was able to start up from my ubuntu live cd, mount my hard drive and veiw a few of my files, but when I try to open up most of them an error window pops up that says I don't have permission to veiw them. Since I did have some advance warning I was able to make back-up copies of all my most important files, but there are still a few things on there I'd like to save before I scrap my old hard drive. But, as a Linux newbie, I'm a little stumped.  Is there a disk troubleshooting/ recovery utility included or accessible from the live cd that I can use to try and recover my files?

Thanks for your help!

---

### Post by cm.squared on 2008-04-14
Have you tried using sudo to access the files that give you a permission denied message?

---

### Post by cm.squared on 2008-04-14
Otherwise, if that doesn't work [this page]("https://help.ubuntu.com/community/DataRecovery?highlight=%28recover%29") looks promising.

Also, make sure that you are mounting your drives read only so you don't inadvertantly overwrite anything.

---

