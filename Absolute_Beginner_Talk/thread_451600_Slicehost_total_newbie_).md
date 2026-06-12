---
title: "Slicehost total newbie :)"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by woodyuk on 2007-05-22
Hi

I have have recently moved from Windows (over 15 years using!) to a Mac and started coding in Ruby for Rails.  I have just signed up for hosting with Slicehost and got my slice today! ya! its so cool!  So pleased I have moved away from Windows, however this is one steep learning curve!

I have managed to upgrade my slice to 7.04 and got Rails and apache 2.2 installed - quite impressed with myself :-)  Everything is done through SSH / Bash, no interfaces!

However i am stuck with three  really silly problems.

1. I created a new user called Woody which has sudo rights.  I have installed apache 2.2 and using WinSCP download the .conf file to edit.  I tried to upload the .conf back to the apache directory and its clear I don;t have the rights.  It works fine if I use root, but thats bad and need to work out how to change rights for a user.  Now I guess I could use chmod and make the apache direct RW for everyone? Is that the best way ? or should I be using groups ?

2. I want to setup a VPN Server, so i can VPN from my Mac > slicehost - also means I can be seen external from a US IP address which is cool for various reasons.  Is their a guide for setting this up?

3. How can I setup a SSH Key rather than password to login, I have one for my work access (Solaris) however no idea how its all setup.  Is their a good guide for this.

Thanks for any help and you might see me around on here!

Woody

---

### Post by Pragmatist on 2007-05-25
Do these links help?:

[https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles](https://help.ubuntu.com/community/EnablingUseOfApacheHtaccessFiles)

[https://help.ubuntu.com/community/SSH_VPN?highlight=%28vpn%29](https://help.ubuntu.com/community/SSH_VPN?highlight=%28vpn%29)

---

