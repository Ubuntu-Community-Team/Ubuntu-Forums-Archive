---
title: "Edgy to Fiesty"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by rosswmcgee on 2007-03-29
I have had no problems with ubuntu edgy 6.10. If I upgrade to the new feist 7.04 does that mean a complete new install and loss of current data?:)

---

### Post by Fenrirwulf on 2007-03-29
I was sort of wondering the same thing, just having downloaded the 6.10 iso today. I was going to install it this weekend and then noticed a new release is coming in a couple weeks. Here's what I found out.

[http://www.ubuntuforums.org/showthread.php?t=395816&highlight=feisty+upgrade](http://www.ubuntuforums.org/showthread.php?t=395816&highlight=feisty+upgrade)

Hope that helps!

---

### Post by smile-its-smiley on 2007-03-29
it does mean you will loose all your data so back it up

---

### Post by Delvien on 2007-03-29
> **smile-its-smiley said:**
> it does mean you will loose all your data so back it up

?????

 That is not correct sir.


If you upgrade on a current Edgy install, adding the correct repos, and doing a dist-upgrade, you will not lose personal data.

BUT BE WARNED, since Feisty is still in beta, it is unstable, and should not be installed if you are a beginner.

---

### Post by bodhi.zazen on 2007-03-29
You can upgrade to Feisty without data loss.

Here's how :

[https://help.ubuntu.com/community/FeistyUpgrades](https://help.ubuntu.com/community/FeistyUpgrades) 

I would wait until Feisty is released and see if there are problems (wait a week or two).

---

### Post by ricardisimo on 2007-03-29
I did the upgrade from Edgy to Feisty via the correct and official method, and there is no data loss. That said, I would also wait for the final release. We are talking about one month here, and I think it's worth it to you to wait.

The fact that Edgy is working fine for you should seal the deal. Edgy was a total mess on my comp, which is why I went ahead and did it... that, and I'm none too bright. :-)

---

### Post by rosswmcgee on 2007-03-29
I have a spare computer that has linspire 5.0 on it. All is well there. I guess I will wait and  install Feisty  on it when it comes out. I heard the printer/scanner installs on Feisty are very good. Usually that is a hard one to do. Hope they are right and thanks for the info, I am no whiz either.

---

### Post by chocbar31 on 2007-03-29
No data loss. Backup anyway though...time saver all the same.

Feisty runs much smoother on my Dell Inspiron 9100 w/Intel wireless 2100. No reconfigurations needed...especially for WPA, which "Just Worked!" 

Mostly everything just works now....Can M$ say that? NOPE! Need drivers for lots of stuff.

However, if you have Automatix installed, you may wanna go fresh. Come to think of it...I did have issues when Automatix was installed on my first attempt. Some packages were skipped as Automatix makes changes to the sources (I heard through the grapevine). The second attempt was a breeze without Automatix.

---

### Post by Yoooder on 2007-03-29
Since the question at hand has been answered: let me share my experience in doing upgrades from Edgy to Feisty...

  fyi:  To do my upgrades I opened a terminal then:
1) switched to root
> sudo su

2) used the update manager to automatically upgrade for me
> update-manager -c -d

I've performed this upgrade on 2 seperate machines.  The first had Edgy installed only very briefly, and was not customized, while the second was heavily customized in Edgy and was heavily used.

The first (a fresh Edgy install straight to the upgrade) worked wonderfully, and even though I was using an alpha version of Feisty, it seemed quite stable

The second (the heavily tweaked/used Edgy box) was not so smooth.  The upgrade itself was easy, but I had to reconfigure many of my customizations (notably: mdadm, lvm2, and my mythtv is still in a semi-broke state).

The two boxes were running Feisty at the same time, and were both up to date--so I found it interesting that the clean(er) install seemed much more stable than my used install.  I've been meaning to do a clean install on my 2nd box to see if the problems are related to my software blend or the upgrade.

---

### Post by maxamillion on 2007-03-29
I have recently performed an upgrade from Edgy to Feisty with many custom applications installed (its my desktop at work) and all I had to do was resolve a few dependencies after the update due to the non-standard (outside the repositories) applications but other than that everything went smoothly ... I didn't lose any data or any settings.

---

