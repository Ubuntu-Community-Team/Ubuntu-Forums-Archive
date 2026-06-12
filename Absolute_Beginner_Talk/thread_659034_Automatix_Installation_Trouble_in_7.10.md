---
title: "Automatix Installation Trouble in 7.10"
date: 2008-01-05
forum: Absolute Beginner Talk
---

### Post by Mikey Daniels on 2008-01-05
I have tried to download Automatix for 7.10 but came across error messages and the package doesn't work.

When trying to play a DVD I get the message:

Cannot install 'gstreamer0.10-plugins-ugly'

This application conflicts with other installed software. To install 'gstreamer0.10-plugins-ugly' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.

I have looked at the Forum and run the following items as suggested and get the following responses:

mike@mike-desktop:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main" | sudo tee -a /etc/apt/sources.list 
[sudo] password for mike: 
Sorry, try again. 
[sudo] password for mike: 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) gutsy main 
mike@mike-desktop:~$ wget [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key) 
--13:29:07--  [http://www.getautomatix.com/keys/automatix2.key](http://www.getautomatix.com/keys/automatix2.key) 
           => `automatix2.key' 
Resolving [www.getautomatix.com](www.getautomatix.com)... 216.120.255.9 
Connecting to www.getautomatix.com|216.120.255.9|:80... connected. 
HTTP request sent, awaiting response... 200 OK 
Length: 1,706 (1.7K) [application/pgp-keys] 

100%[====================================>] 1,706         --.--K/s             

13:29:07 (2.63 MB/s) - `automatix2.key' saved [1706/1706] 

mike@mike-desktop:~$ gpg --import automatix2.key 
gpg: directory `/home/mike/.gnupg' created 
gpg: new configuration file `/home/mike/.gnupg/gpg.conf' created 
gpg: WARNING: options in `/home/mike/.gnupg/gpg.conf' are not yet active during this run 
gpg: keyring `/home/mike/.gnupg/secring.gpg' created 
gpg: keyring `/home/mike/.gnupg/pubring.gpg' created 
gpg: /home/mike/.gnupg/trustdb.gpg: trustdb created 
gpg: key E23C5FC3: public key "Arnav Ghosh (Automatix Team Lead) <greyrod@gmail.com>" imported 
gpg: Total number processed: 1 
gpg:               imported: 1 
mike@mike-desktop:~$ gpg --export --armor E23C5FC3 | sudo apt-key add 
gpg: can't open `': No such file or directory 
mike@mike-desktop:~$ sudo apt-get update 
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/main Translation-en_GB 
Ign cdrom://Ubuntu 7.10 _Gutsy Gibbon_ - Release amd64 (20071016) gutsy/restricted Translation-en_GB 
Get: 1 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release.gpg [189B]                 
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Translation-en_GB 
Get: 2 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release [6738B] 
Ign [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release 
Get: 3 [http://www.getautomatix.com](http://www.getautomatix.com) gutsy/main Packages [1751B] 
Fetched 8678B in 0s (9521B/s)  
Reading package lists... Done 
W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) gutsy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3 
W: You may want to run apt-get update to correct these problems 
mike@mike-desktop:~$ sudo apt-get install automatix2 
Reading package lists... Done 
Building dependency tree       
Reading state information... Done 
Some packages could not be installed. This may mean that you have 
requested an impossible situation or if you are using the unstable 
distribution that some required packages have not yet been created 
or been moved out of Incoming. 

Since you only requested a single operation it is extremely likely that 
the package is simply not installable and a bug report against 
that package should be filed. 
The following information may help to resolve the situation: 

The following packages have unmet dependencies. 
  automatix2: Depends: tango-icon-theme-common but it is not installable 
              Depends: tango-icon-theme but it is not installable 
E: Broken packages 
mike@mike-desktop:~$ 

At the moment I can't play DVDs and when I try to look at videos on YouTube I get "Additional Pug ins are required to display all the media on this page. I click the "Install missing Plugins" request and click to install Adobe Flash Player Installer but the process doesn't work. Can anyone help me so that  can get up to speed in installing whatever is needed to allow me to view DVDs and run videos on YouTube?

Thanks

Mike

---

### Post by rainwalker on 2008-01-05
I wouldn't recommend using Automatix, it can mess with a lot of things.

Have you tried installing the Ubuntu Restricted Extras?
Also, I think Flash installation is broken at the time, because Adobe changed the file that the download link uses, and there isn't an official fix yet.

---

### Post by Mikey Daniels on 2008-01-05
> **rainwalker said:**
> I wouldn't recommend using Automatix, it can mess with a lot of things.

Have you tried installing the Ubuntu Restricted Extras?
Also, I think Flash installation is broken at the time, because Adobe changed the file that the download link uses, and there isn't an official fix yet.

Where can I find the Ubuntu Restricted extras? How do I install them?

Thanks

Mike

---

### Post by rainwalker on 2008-01-05
Go to Applications > Add/Remove and search for it
Make sure you have the restricted and multiverse repositories enabled (System > Administration > Software sources)

Also, for DVDs, try installing libdvdcss from [http://packages.medibuntu.org/pool/free/libd/libdvdcss/](http://packages.medibuntu.org/pool/free/libd/libdvdcss/)

---

### Post by MattBD on 2008-01-05
I found the easiest way to get DVD playback running in Gutsy was as follows:

1) Install the Ubuntu restricted extras metapackage - just open a terminal and enter sudo apt-get install ubuntu-restricted-extras.

2) Then use the install-css shell script - just enter sudo /usr/share/doc/libdvdread3/install-css.sh.

I was using Kubuntu Gutsy so I installed kubuntu-restricted-extras, but I think it should be exactly the same otherwise.

I had very bad experiences with Automatix in Feisty, but I think Gutsy is a big improvement. There's very little you need Automatix for now, and quite frankly I'd steer clear of it if you can. Some people have had no problems with it at all, but it caused me no end of trouble.

---

