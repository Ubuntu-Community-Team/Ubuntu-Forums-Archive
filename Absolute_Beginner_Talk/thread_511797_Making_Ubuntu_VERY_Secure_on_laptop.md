---
title: "Making Ubuntu VERY Secure on laptop"
date: 2007-07-28
forum: Absolute Beginner Talk
---

### Post by JAYCEE1 on 2007-07-28
I getting a Dell latitude c400 laptop with Ubuntu already installed by previous owner. 

How do I make it as secure as possible? I'd like to surf using dialup and Wifi through Tor & Privoxy. On my previous laptop, I could only run these with a root terminal open. That did not work out well. 

I want to prevent outsiders from getting into my computer and also prevent trojans, loggers, etc from being put on my HD. 

Where do I start?

Thanks!

---

### Post by Koybe on 2007-07-28
I think you should start with firewalling. Iptables does it pretty well and firestarter is a easy frontend for it. ;)

---

### Post by Jimmyfj on 2007-07-28
Well if you want more security that already provided by Ubuntu you could install Bastille Linux and run the setup. Please be advised that Bastille is NOT for beginners.

---

### Post by roaldz on 2007-07-28
I think you're not so easy to attack if you're not running everything as root:) Chroot some things down, think about file permissions (samba shares). I think that a standard ubuntu installation with a good password is secure enough for about 95% of the users.

---

### Post by .bashrc on 2007-07-28
Dial up, eh. 

Well, if you have wifi access, then securing your access point should be a high priority anyhow. I am sure others have some good suggestions, but might I start with:

1. Strong passwords
2. WPA
3. MAC address filtering
4. SSID broadcasting off
5. private IP space (not default router one)

along with:
if you don't need ssh, knock down sshd. Use TCP wrappers if you have to use ssh. Turning any/all sharing protocols off. Don't go to shady websites. Don't click on spam links in your email :). VPN.

Oh yeah, and in regard to that crazy root thing (!), don't even give your normal user account sudo privileges. It's kind of a P.I.T.A. in practice but it's saved me at least once.

---

### Post by JAYCEE1 on 2007-07-28
> **.bashrc said:**
> Dial up, eh. 

Well, if you have wifi access, then securing your access point should be a high priority anyhow. I am sure others have some good suggestions, but might I start with:

1. Strong passwords
2. WPA
3. MAC address filtering
4. SSID broadcasting off
5. private IP space (not default router one)

along with:
if you don't need ssh, knock down sshd. Use TCP wrappers if you have to use ssh. Turning any/all sharing protocols off. Don't go to shady websites. Don't click on spam links in your email :). VPN.

Oh yeah, and in regard to that crazy root thing (!), don't even give your normal user account sudo privileges. It's kind of a P.I.T.A. in practice but it's saved me at least once.



Dialup at home, Wifi/wardriving on the road. I notice you say "Strong" password. I'd be totally embarrassed to tell you what the root password was. Perhaps that was my whole problem?

I have thought of just running from a live-cd using a flash drive for swap file to store preferences. It seems that you couldn't get much more secure than a read-only boot volume. Then again, maybe I'll try real passwords.

---

### Post by .bashrc on 2007-07-28
> **JAYCEE1 said:**
> Dialup at home, Wifi/wardriving on the road. I notice you say "Strong" password. I'd be totally embarrassed to tell you what the root password was. Perhaps that was my whole problem?

I have thought of just running from a live-cd using a flash drive for swap file to store preferences. It seems that you couldn't get much more secure than a read-only boot volume. Then again, maybe I'll try real passwords.

lemme guess 4:

1. root
2. jaycee
3. (insert your dog's name here)
4. (blank)

:)

strong passwords are not unbreakable but it's much much more difficult.

---

### Post by BobCFC on 2007-08-31
[Here]("https://help.ubuntu.com/community/TOR") is a guide to setup TOR and privoxy on Ubuntu

You can switch TOR on and off using a button on firefox if you have the [TOR firefox plugin]("https://addons.mozilla.org/en-US/firefox/addon/2275")



There are also security distros with tor as a livecd such as   Anonym.OS

---

### Post by bodhi.zazen on 2007-08-31
Well, the most important step is to re-install the OS.

Second is there is no such thing as secure if one has physical access to the laptop. I would advise you encrypt your root partition and swap.

	[https://help.ubuntu.com/community/EncryptedFilesystem](https://help.ubuntu.com/community/EncryptedFilesystem)

	[https://help.ubuntu.com/community/EncryptedFilesystemHowto](https://help.ubuntu.com/community/EncryptedFilesystemHowto)

	[http://www.howtoforge.com/truecrypt_data_encryption](http://www.howtoforge.com/truecrypt_data_encryption)

Third, see this thread : [http://ubuntuforums.org/showthread.php?&t=510812](http://ubuntuforums.org/showthread.php?&t=510812)

Tor is easy to setup : [https://help.ubuntu.com/community/TOR](https://help.ubuntu.com/community/TOR)

---

