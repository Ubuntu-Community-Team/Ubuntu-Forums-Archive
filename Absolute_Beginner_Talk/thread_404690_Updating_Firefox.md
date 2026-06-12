---
title: "Updating Firefox"
date: 2007-04-08
forum: Absolute Beginner Talk
---

### Post by kfehr911 on 2007-04-08
From what I know old Dapper Drake uses Firefox version 1.5.0.11.  I would like to upgrade it to Firefox 2.0.  I have already downloaded the new version and I don't know how to install it. I know that are is a way to swap files but I can't remember the process.  Any hint or help out there? Thanks

---

### Post by Maestro23 on 2007-04-08
[https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29](https://help.ubuntu.com/community/FirefoxNewVersion?highlight=%28firefox%29)

---

### Post by heimo on 2007-04-08
These should help:
[http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)
[https://help.ubuntu.com/community/FirefoxNewVersion](https://help.ubuntu.com/community/FirefoxNewVersion)

---

### Post by Happy_Man on 2007-04-08
Try [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox)

---

### Post by kfehr911 on 2007-04-08
Thanks folks! The link to [http://www.psychocats.net/ubuntu/firefox](http://www.psychocats.net/ubuntu/firefox) worked great I used the automated install and it worked great except for the fact that I a newbie and I still do funny little things that make easy thing hard.

---

### Post by Guns90 on 2007-04-15
Hello all.  I just tried to update Firefox using the psychocats link.  Here is what happened:

gary@Faith:~/Desktop$ cd ~/Desktop
gary@Faith:~/Desktop$ chmod +x installnewfirefox.sh
gary@Faith:~/Desktop$ ./installnewfirefox.sh
The most recent release of firefox is detected to be 2.0.0.3. Please make sure this is correct before proceeding. (You can confirm by going to [http://www.mozilla.com/](http://www.mozilla.com/)) Is it correct [y/n]? y
Please choose the localization (language) for firefox. Enter the number of your choice from the list below. [If you do not see a list of localizations, please contact [email]nanotube@users.sf.net[/email], and we will try to track down the problem.]
0: af
1: ar
2: be
3: bg
4: ca
5: cs
6: da
7: de
8: el
9: en-GB
10: en-US
11: es-AR
12: es-ES
13: eu
14: fi
15: fr
16: fy-NL
17: ga-IE
18: gu-IN
19: he
20: hu
21: it
22: ja
23: ka
24: ko
25: ku
26: lt
27: mk
28: mn
29: nb-NO
30: nl
31: nn-NO
32: pa-IN
33: pl
34: pt-BR
35: pt-PT
36: ru
37: sk
38: sl
39: sv-SE
40: tr
41: zh-CN
42: zh-TW
Enter your choice of localization: 10
You have chosen localization "en-US". Is that correct [y/n]? y

Updating repositories list

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Get:1 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Get:3 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release.gpg [191B]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release.gpg [189B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) dapper/multiverse Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/universe Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-backports/multiverse Packages
Fetched 4B in 0s (5B/s)
Reading package lists... Done

Making sure libstdc++5 and the Ubuntu Firefox package are installed

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

Backing up old Firefox preferences


Changing to home directory


Downloading Firefox archive from the Mozilla site

--16:23:20--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz)
           => `firefox-2.0.0.3.tar.gz'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz) [following]
--16:23:21--  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz)
           => `firefox-2.0.0.3.tar.gz'
Resolving releases.mozilla.org... 64.50.236.52, 64.50.236.214
Connecting to releases.mozilla.org|64.50.236.52|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.

The next step will verify the GPG signature for the firefox archive to assure its integrity. This step is important for your security. However, if you have problems getting this to work right, you may choose 'no' and proceed to installation without signature verification. Do you want to verify the signature [y/n]?y

Downloading Firefox signature from the Mozilla site

--16:23:31--  [http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://ftp.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc)
           => `firefox-2.0.0.3.tar.gz.asc'
Resolving ftp.mozilla.org... 63.245.208.138
Connecting to ftp.mozilla.org|63.245.208.138|:80... connected.
HTTP request sent, awaiting response... 302 Found
Location: [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc) [following]
--16:23:31--  [http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc](http://releases.mozilla.org/pub/mozilla.org/firefox/releases/2.0.0.3/linux-i686/en-US/firefox-2.0.0.3.tar.gz.asc)
           => `firefox-2.0.0.3.tar.gz.asc'
Resolving releases.mozilla.org... 64.50.236.214, 64.50.236.52
Connecting to releases.mozilla.org|64.50.236.214|:80... connected.
HTTP request sent, awaiting response... 416 Requested Range Not Satisfiable

    The file is already fully retrieved; nothing to do.


Importing Mozilla Software Releases public key

Note that if you have never used gpg before on this system, and this is your first time running this script, there may be a delay of about a minute during the generation of a gpg keypair. This is normal and expected behavior.

gpg: requesting key 1AF32821 from hkp server subkeys.pgp.net
gpg: key 0E3606D9: "Mozilla Software Releases <releases@mozilla.org>" not changed
gpg: Total number processed: 1
gpg:              unchanged: 1

Verifying signature...
Note: do not worry about "untrusted key" warnings. That is normal behavior for newly imported keys.

gpg: Signature made Tue 20 Mar 2007 03:52:21 AM EDT using DSA key ID 0E3606D9
gpg: Good signature from "Mozilla Software Releases <releases@mozilla.org>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: F57F 372A 8C6D 4F55 72DE  C9B9 696E 3431 0E36 06D9

Extracting the downloaded Firefox archive

tar: /opt: Cannot chdir: No such file or directory
tar: Error is not recoverable: exiting now
Previous command did not complete successfully. Exiting.
gary@Faith:~/Desktop$

I guess that I'm still too stupid to understand this stuff.  Can I get a little help please? Thanks

---

### Post by klytu on 2007-04-15
Try typing this into a terminal window(or copy and paste): ```
 sudo mkdir /opt
```
Then run the installnewfirefox script again.

---

### Post by Guns90 on 2007-04-15
klytu, I was thinking that the create /opt directory was a line omitted in the tar.  That did the trick, though.  THank you much.

---

### Post by geezerone on 2007-04-16
I updated from 1.5 to 2.0.0.2 some time ago via the link above but the option to check for updates is missing and hasn't updated to 2.0.0.3 since it has been released. Any ideas?

TIA:D

---

### Post by klytu on 2007-04-16
> **geezerone said:**
> I updated from 1.5 to 2.0.0.2 some time ago via the link above but the option to check for updates is missing and hasn't updated to 2.0.0.3 since it has been released. Any ideas?

TIA:D

Try ```
sudo firefox
``` then check for updates. While running firefox in sudo mode, ONLY check for updates - do not visit any websites or surf the internet. When the update completes (assuming it does) close firefox and re-open it as a normal user. The link in your signature has details. ;-)

---

### Post by geezerone on 2007-04-16
Thanks it worked but had to carry out full install rather than partial update.

Now on latest version! :D

---

