---
title: "faied to run /usr/sbin/synaptic"
date: 2007-06-20
forum: Absolute Beginner Talk
---

### Post by baekeland on 2007-06-20
I have Windows XP already Installed and everything moved along as it should do.  When I booted into Ubuntu, I was expecting to be hit with the automatic updates.  This did not occur.  So I went and tried doing it (updates) manually.  All went well, it even asked for my password and then I was hit with the following message -- which I have never come across before:

[B][B][CENTER][B][SIZE="4"][SIZE="5"]Failed to run /usr/sbin/synaptic '--hide-main-window' '--non-interactive' '--parent-window-id' '39845891' '--progress-str' 'Please wait, this can take some time.' '--finish-str' 'Update is complete' '--set-selections-file' '/tmp/tmpVrJc63' as user root.
[/B]
The underlying authorization mechanism (sudo) does not allow you to run this program. Contact the system administrator.[/SIZE][/SIZE][/B][/CENTER][/B]

I looked around the boards and was unable to find this "error."  My question is is this easily corrected, if so how do I do it and I do not wish to mess up the Grub between Ubuntu 7.04 and WindowsXP if I reinstall Windows XP.

Does anyone have any advice for what appears as mysterious and strange to myself.

Thanks so Kindly,

Antony  :D

---

### Post by lamalex on 2007-06-20
I don't think reinstalling XP is going to help much. Probably just make new problems. it looks like your sudoers file or permission on /usr/sbin/synaptic got messed up. can you do an ls -lah /usr/sbin/ |grep synaptic and paste the output?

---

