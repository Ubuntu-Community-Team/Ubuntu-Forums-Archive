---
title: "[SOLVED] ltsp, can't get x"
date: 2007-11-11
forum: Absolute Beginner Talk
---

### Post by farifk on 2007-11-11
I'm a novice here, so bare with me.
I'm currently trying to implement ltsp using Ubuntu 7.10 in my office.
Before I continue further let me tell you my server/client situation:
My server is amd 64 athlon 3000+ system with 1 GB of RAM. 80 GB of hardrive, running Ubuntu 7.10 64 bit
My clients mostly are pentium 3 with more or less 64 to 128 MB of RAM
And here is the story, and my progress so far:
I followed the quick install procedure, but it has problems, and my progress has been very slow.
First of all was of the build client. After looking at many forum sites, I just realized that I have build the wrong client. so i have done the ltsp-build-client --arch i386 to build the correct architecture for my clients. That was already done. Using the guide from ubuntu community forum [https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup](https://help.ubuntu.com/community/UbuntuLTSP/LTSPCrossArchSetup)
doesn't help, I don't know which version of ubuntu/ltsp that is covered by that guide.
Second, I changed some of the setting in the /etc/inetd.conf and /etc/ltsp/dhcpd.conf with no luck, but luckily, when I set it to the default values, everything went fine (my client can boot from the PXE, and able to find the needed files).
Now, the problem is, although the client is able to boot from PXE, it doesn't get very far. The log in /var/log/syslog doesn't say any error, but the booting sequence just stop at initramfs, and nothing more. So the client just sit there with initramfs prompt. From here, I have no idea how to make the clients to boot the X and everything else.
What should i do? can you be more specific in our answer? I'm pretty much new to Ubuntu.

Thanks
Frank

---

### Post by Lem on 2007-11-12
This might help;

[http://ubuntuforums.org/showthread.php?t=610695](http://ubuntuforums.org/showthread.php?t=610695)

---

### Post by farifk on 2007-11-13
I've rebuild the client several times, and it looks fine, no error. I did setup the gdm through gdmsetup, turn on the remote login the same as local login. but still nothing. I do have the same <initramfs> prompt whenever i boot my sony srx-7 with Ubuntu 7.10 cd. Let me try boot the PXE from other computer, who knows, may it's just my sony that isn't right.
let me know if there is something else that i miss.
btw, my sever ip is 192.168.7.202
i did the changes in dhcpd.conf as stated in my previous post.
thanks anyway. keep it up

---

### Post by Lem on 2007-11-13
> **farifk said:**
> I did setup the gdm through gdmsetup

Is this something that you are running in chroot?, or does your server have no x session?

I'm not entirely sure if LTSP works on a server with out x, and secondly there should be no reason to run gdmsetup on the chroot'ed environment as it sets up ldm by default. (Like GDM but LTSP specific)

---

### Post by farifk on 2007-11-13
GOT IT :)
i did the lts.conf setting, i put it in the folder /var/lib/tftpboot/i386/lts.conf
it does do something. but it turns out that my firewall do most of the blocking.
i already open the correct port for 2001 (for i386.img), but it turns out it is not enough. i have to open up everything else, such as xwindows 6011, ltspfs 9220, ssh 22, 9571, 9572, syslog 514, dhcp 67-68, http 80, nfs 111 2049. after i did all of this, viola everything runs great.
what got me in to that conclusion is that i decided to delete "splash" and "quiet" setting in  /var/lib/tftpboot/i386/pxeconfig.cfg/default. and it turns out that the PXE boot sequence stopped when trying to find some files in the server, that is why it stopped and get into the initramfs prompt.
after i turn on the firestarter i realized of those blocked ports, thus i add them to the policy, and that is it.
now my problem is, the x is creating a small window in my srx-7, not full screened X. anything on that?

---

### Post by SpiritIsReality on 2007-11-13
just some links
[http://ubuntuforums.org/showthread.php?t=608744&highlight=ltsp+documentation](http://ubuntuforums.org/showthread.php?t=608744&highlight=ltsp+documentation)

---

