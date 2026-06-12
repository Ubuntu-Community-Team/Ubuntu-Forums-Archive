---
title: "[SOLVED] Networking gurus: can you help"
date: 2008-02-25
forum: Absolute Beginner Talk
---

### Post by t.septekin on 2008-02-25
I have two laptops: an hp Pavilion running Feisty, and a Sony Vaio  now running Hardy, connected via a Wireless router.

Initially I had the Gutsy in Vaio: I could access the shared home folder and a shared drive in it from Pavilion, no problem. However, I could not access the shared folders in Pavilion from Vaio; Vaio would not even ask for the authentication password.

This morning I installed Hardy Heron in the Vaio. Now, neither laptop will access the other.

I booted the Pavilion into Windows XP: the Vaio accessed Pavilion's shared drive happily, reading and writing.

I have no wish to run Windows again, I'm keeping it in one laptop just in case I need to access old files which are not compatible.

Somewhere I must be doing something basically -if not idiotically- wrong. Can anyone help me to sort this out, please?

BTW, smb.conf and smbpasswd seem to be ok in both machines.

---

### Post by uberlube on 2008-02-25
Just out of curiosity, how did you have them connected in the first place? I am trying to have a shared folder on my desktop that my laptop can grab from. Sorry for changing your subject.

---

### Post by t.septekin on 2008-02-25
I have them connected through a wireless router normally.

---

### Post by uberlube on 2008-02-25
No, sorry I meant how are you able to share files between them.

---

### Post by t.septekin on 2008-02-25
I followed the instructions in the following:

[http://www.youtube.com/watch?v=Ad17kma8rNM](http://www.youtube.com/watch?v=Ad17kma8rNM)

[http://maddhat.com/?p=13](http://maddhat.com/?p=13)

---

### Post by Mauler5858 on 2008-02-26
Is there a firewall set up on either one?

---

### Post by t.septekin on 2008-02-27
Nay.

---

### Post by TheDilettante on 2008-02-27
[https://help.ubuntu.com/community/SettingUpNFSHowTo](https://help.ubuntu.com/community/SettingUpNFSHowTo)  <- Have you tried that?  It's been awhile since I networked two 'buntu machines, but I had to use NFS.  It looks a little scary, but it took me like 10 minutes actually...

---

### Post by hyper_ch on 2008-02-27
or you could use SSHFS:  [https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

If your wifi is not encrypted then SSHFS will encrypt the stuff... however that makes it slower than NFS

---

### Post by cozmicharlie on 2008-02-27
> **t.septekin said:**
> I have two laptops: an hp Pavilion running Feisty, and a Sony Vaio  now running Hardy, connected via a Wireless router.

Initially I had the Gutsy in Vaio: I could access the shared home folder and a shared drive in it from Pavilion, no problem. However, I could not access the shared folders in Pavilion from Vaio; Vaio would not even ask for the authentication password.

This morning I installed Hardy Heron in the Vaio. Now, neither laptop will access the other.



Why did you install Hardy?  The obvious answer is go back to Gutsy.  Hardy is still under development.

---

### Post by t.septekin on 2008-02-27
For some reason that I cannot comprehend neither Gutsy nor Hardy will install in my hp Pavilion; similarly Feisty will not install in the Sony Vaio. I am now using Hardy in the Sony, knowing very well it is still the development version, because it looks and feels a bit better!

I was attempting to try the three versions in the two machines to see if I could get a combination to communicate better. I am resigned by now to keep the status quo.

By the way, now I am able to browse Sony/Hardy from HP/Feisty but still not the other way.

Sony lists the shared folders or drives in HP but after I enter the authentication key returns "Unable to mount location / Failed to mount Windows share". Sony/Hardy can access the shared folders in HP when latter is running Windows XP.
 
I may, however, give NFS a go. I did not try it before as it is mentioned as an out-of-date system; maybe it still has got life in it.

Thanks to all who tried. I hope to give a final report before closing the thread.

---

### Post by mrc.gran on 2008-02-27
Hi,

1. have you used 'sudo smbpasswd -a [USERNAME]' to add your user to samba share service?
[http://www.samba.netfirms.com/addusers.htm#adduser](http://www.samba.netfirms.com/addusers.htm#adduser)

2. try following these tips:
[http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service](http://ubuntuguide.org/wiki/Ubuntu:Gutsy#How_to_install_Samba_Server_for_files.2Ffolders_sharing_service)

cheers,
M.

---

### Post by mrc.gran on 2008-02-27
two more nice links:

COMMAND LINE:
1. there's a quick step-by-step list on setting up samba shares in ubuntu here:
[http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend](http://www.howtoforge.com/ubuntu-gutsy-samba-standalone-server-with-tdbsam-backend)

GRAPHICALLY:
2. this blog entry shows how to set up samba shares in ubuntu with only one mouse right-click in nautilus (the file manager):
[http://www.alterego7.com/2008/01/howto-share-folders-on-ubuntu-gutsy.html](http://www.alterego7.com/2008/01/howto-share-folders-on-ubuntu-gutsy.html)

---

### Post by sryth on 2008-02-27
If both are running linux, then use NFS.  Easy stuff.  Personally I find samba annoying and only use it when necessary to share with a windows machine.

---

### Post by t.septekin on 2008-02-27
My gratitude to all who suggested NFS. I did not find it too intimidating to install (as per Czar's blog); in fact it has worked smoothly and all is well now.

I do wish that I knew why Samba worked one way but not the other. Yes, I had been adding smbpasswd diligently in both machines, etc, etc.

Thanks once again to all of you who gave their time to help. I shall pour myself a little something to drink to your good healths and well-being, then I will go and remove all traces of Windows XP from my new laptop.

---

