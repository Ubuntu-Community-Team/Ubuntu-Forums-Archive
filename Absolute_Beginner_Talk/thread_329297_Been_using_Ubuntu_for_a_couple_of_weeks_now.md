---
title: "Been using Ubuntu for a couple of weeks now"
date: 2007-01-01
forum: Absolute Beginner Talk
---

### Post by Tutu 1234 on 2007-01-01
Edgy user, installed from livecd from official repository.

I loved how easy it was to install and get running. I have a few issues
1. Is with vlcplayer crashing whenever I go fullscreen and then return to the desktop.
2.  I have a broken package (Something to do with Azureus happened on uninstall, retied reinstalling azureus.)
3. Can't get my pocketpc to sync with activsync in a VM (Couldn't get it to sync under windows native install either.), syncs to my MP3 player alright, lucikly I have a laptop to hand as well with XP on it and syncing works fine on it.
4. Flash card writing seems flaky I;ve lost a few files writing to flash card (How do I check the filesystem on the flash cart?)
5. I keep getting told there a disk manager system->administration-Disks  I don't have one on mine.

6. I've installed realplayer as per instructions on website yet bbcnews streams don't work, I tried installing mozilla addons from automatix still nothing. My downloaded realplayer content works fine on realplayer, mplayer & totem but nothing when streamed. How do I sort this out, this one is my biggest issue.


7. I love the feel of Ubuntu, been thinking of formatting my windows partition and putting another of copy ubuntu on it for emergency use and to end the NTFS hassle once and for by consolidating all my file system on the pc to efs3. How the hell do I edit the dual boot to get rid of the windowsxp boot and replace in with my emergency Ubuntu (Or maybe other flavour of linux)

Any one recommend any decent payroll invoicing software open source would be preferable but stability and accuracy are far more important.

Thanks

---

### Post by mojoman on 2007-01-01
On number 2, try: ```
sudo apt-get install --fix-broken
``` This should sort out broken dependencies. 

On number 5, I think that you can click an option under System-Admininstration-LoginWindow that shows more options under Adminstration (could be "allow local administrator login" under the tab security). Gotta add that I'm not 100% on this, I had the same problem myself but it was a while ago so I don't recall exactly how I fixed it- ;) 

/Mojoman

---

