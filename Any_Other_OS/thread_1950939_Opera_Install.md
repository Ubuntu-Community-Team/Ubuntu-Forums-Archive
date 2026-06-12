---
title: "Opera Install"
date: 2012-04-01
forum: Any Other OS
---

### Post by ken0069 on 2012-04-01
OK so I've got 3 multiboot computers.  Two have Mint and one has Ubuntu 10.10 along with various flavors of Winders.  I'm also on a USB data card internet service that has a byte LIMIT per month.  With the Windowz OS I usually just download the new version of Opera one time and then manually install it via the .exe on each system but I'm having problems doing this with both Mint and Ubuntu??

I just downloaded the new version of Opera and then went to the downloads folder and right clicked on it and selected open with debain package installer and then I get this error?  

Error: Breaks existing package 'opera' conflict: opera ( )

And it doesn't give me any options to do this install??  I understand that there's a conflict with existing stuff but I don't want to "uninstall" Opera and loose all my current settings to get this updated version to install in Mint or Ubuntu?

Any help here as I'm somewhat "challenged" when the command line is involved!

Thanks,

Ken, who HATES Unity enough to switch!  ;-)  And if it's any consolation, I HATE Metro also!

---

### Post by kc1di on 2012-04-01
you can try this in a terminal.
Go to your downloads folder (where you downloaded Opera)
in the terminal type ```
sudo dpkg -i --force Opera-xxxxxx.deb
``` (Replacing thexxxxx with the actual file name)
Warning this may break Opera all together.

you may also want to try using the opera PPA repository. here's how:
[http://shuffleos.com/4270/install-opera-11-60-tunny-ubuntu-1110-1104/]("http://shuffleos.com/4270/install-opera-11-60-tunny-ubuntu-1110-1104/")

---

