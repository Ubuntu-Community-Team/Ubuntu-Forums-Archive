---
title: "[SOLVED] Trouble installing Open Office"
date: 2007-05-22
forum: Absolute Beginner Talk
---

### Post by forestpixie on 2007-05-22
I've tried to get to the bottom of this with other posts but no luck.

I've downloaded open office and extracted it and installed alien 

but trying to use the open office install text is not getting me very far and am confused, I installed it on my pc and I didn't have this trouble.

these are the instructions I'm trying to use

   1.  Unpack the downloaded image into a directory. For example, currently, the following command would unpack into the current directory:
   2. tar xvzf OOo_2.0.4_LinuxIntel_install.tar.gz
   3. su to root, if necessary.
   4. cd into the directory with the unpacked image. This could be RPMS.
   5. Delete any rpm files that do not apply to your system. For example, on a Fedora Core 3 system, delete any rpms specific to another distribution such as openofficeorg-suse-menus-1.9.79-1.noarch.rpm.
   6. Then execute rpm -Uvih *rpm.

once I've got to 5 I have 29 different rpm packages, in desktop-integration there is 1 debian folder and some others - fedora, suse etc

I also seem to have an American version - the one I downloaded previously was English English.


Very confused now - have I downloaded the wrong files?

Or can I get it on the system?

Help would be much appreciated indeed

---

### Post by PlatoDan on 2007-05-22
Are you installing it that way for a reason? Because it might be easier to go through Synaptic (System->Administration->Synaptic Package Manager -> Search for openoffice and install it that way.)

---

### Post by forestpixie on 2007-05-22
I'd had some problems on my pc with mine and had used various threads in the forum to get to download and install the official ver from open office.

What I think is rally confusing me is that I'd downloaded and extracted it before and from there I had debian installer ( I believe) and it took one double click and was presented with a do you want to install box!

Only been doing this for a couple of weeks - and now I have sorted my son's pc I wanted to put the same ver on his - before I got the "Dad it won't work" - his is online at the moment but it won't be for a while once I've got this sorted.

---

### Post by _simon_ on 2007-05-22
Unless I'm missing something OpenOffice is installed by default along with Ubuntu.

It should already be in Applications -> Office

Feisty comes with version 2.2.0

---

### Post by forestpixie on 2007-05-22
yes I know - but I'd had some problems with mine and had uninstalled the default ubuntu version and reinstalled the version from openoffice.

Trying to shut door before horse bolts and to do same with this pc before I get whiny noises from son!

I'm extremely confused because it was much simpler than this a week ago.

---

### Post by tgoose on 2007-05-22
It should be a lot easier just to click on the top panel in Ubuntu

System > Administration > Synaptic Package Manager

and then search for openoffice and select openoffice.org and openoffice.org-l10n-en-gb

That way you get software specifically compiled for Ubuntu, rather than a generic Linux one, and it all works automatically rather than having do do any command line stuff (although ```
sudo aptitude install openoffice.org openoffice.org-l10n-en-gb
``` will work just as well)

---

### Post by _simon_ on 2007-05-22
What were the problems that you had with the Ubuntu installed version, if you don't mind me asking?

---

### Post by forestpixie on 2007-05-22
thanks everyone - I'll just leave it as it is for the moment then I think

---

### Post by forestpixie on 2007-06-07
Got it sorted with this [http://bodmas.org/blog/?p=523](http://bodmas.org/blog/?p=523).

---

