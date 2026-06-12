---
title: "[SOLVED] ClamAV/TK help"
date: 2007-08-19
forum: Absolute Beginner Talk
---

### Post by Akuma Shiro on 2007-08-19
I know everyone says that Linux doesn't need an anti virus program...
"Isn't needed", "waste of resources and ram" blah blah blah
but I want to make sure.
I installed "graphical front-end for ClamAV 
ClamTk is a GUI front-end for ClamAV using perl-Gtk2.
Homepage: [http://clamtk.sourceforge.net/](http://clamtk.sourceforge.net/)
Version: 2.31-0ubuntu1 (clamtk)"
from add/remove, and I also installed some stuff from synaptic that i read on the forum, and nothing I do works.

When I start the program, I get this window.
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/Screenshot-clamtk.png[/IMG]

then when I try to scan my home folder, I get this window.
[IMG]http://i53.photobucket.com/albums/g50/Akuma_Shiro/Screenshot-clamtk-1.png[/IMG]

So, I went into terminal, and typed in what it told me. And here is what I got.

```
 troy@navi1L:~$ sudo freshclam -v
Password:
Current working dir is /var/lib/clamav/
Max retries == 5
ClamAV update process started at Sun Aug 19 14:40:28 2007
Querying current.cvd.clamav.net
TTL: 208
Software version from DNS: 0.91.1
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Local version: 0.90.2 Recommended version: 0.91.1
DON'T PANIC! Read http://www.clamav.net/support/faq
main.cvd version from DNS: 44
main.inc is up to date (version: 44, sigs: 133163, f-level: 20, builder: sven)
daily.cvd version from DNS: 4001
Retrieving http://db.local.clamav.net/daily-4001.cdiff
Ignoring mirror 209.170.150.7 (too often connections with outdated version)
Trying host db.local.clamav.net (216.24.174.245)...
Trying to download http://db.local.clamav.net/daily-4001.cdiff (IP: 216.24.174.245)
Downloading daily-4001.cdiff [100%]
cdiff_apply: Parsed 21 lines and executed 21 commands
Removing backup directory ./clamav-6b3154d5146f2b03908822afb425f632
daily.inc updated (version: 4001, sigs: 14615, f-level: 20, builder: ccordes)
WARNING: Your ClamAV installation is OUTDATED!
WARNING: Current functionality level = 15, recommended = 20
DON'T PANIC! Read http://www.clamav.net/support/faq
Database updated (147778 signatures) from db.local.clamav.net (IP: 216.24.174.245)
troy@navi1L:~$
```All I can gather, is that it is out of date. In synaptic, I didn't see anything that liked like a definition file.
I am out of ideas.

---

### Post by Gremlinzzz on 2007-08-19
clamav is in synaptic package manager

---

### Post by Gremlinzzz on 2007-08-19
> **Gremlinzzz said:**
> clamav is in synaptic package manager

ClamTk too

---

### Post by Hobo Joe on 2007-08-19
Try Firestarter.

But I still say that it isn't needed. :)

---

### Post by Gremlinzzz on 2007-08-19
Also get chkrootkit which is in synaptic package manager to use it after install
sudo chkrootkit

---

### Post by euler_fan on 2007-08-19
Uninstall it. The best way to do ClamAV is from source. The software is well documented but I'm going to change the basic instructions some for extra security.

Go to add/remove applications and get the GPG program for your windows manager. I use Seahorse which works great for Gnome, but there is another one for KDE. They're under Accessories. You need this to verify the cryptographic signature files you are going to be working with.

get into the command line and do as follows:

```
wget http://freshmeat.net/redir/clamav/29355/url_tgz/clamav-0.91.1.tar.gz

wget http://downloads.sourceforge.net/clamav/clamav-0.91.1.tar.gz.sig

wget http://www.clamav.net/gpg/tkojm.gpg

gpg --import tkojm.gpg

gpg --verify clamav-X.XX.tar.gz.sig
```

replace the X.XX with the version number--0.91.1

IF upon completion of the last command the output indicates the signature, then and ONLY THEN will you continue with these instructions. If you do not get a good signature file, go into your home folder, delete the file you just downloaded, and start over again.

Should you get the response you are looking for, proceed as follows:

Download the install instructions from [here]("http://www.clamav.net/doc/latest/clamdoc.pdf") and follow the directions. Any terminal command that starts with a $ put in as seen. Anything following a # you need to use sudo for.

The instructions are very good, just do section 3.3 before section 3.2. Where it says to unpack the package, you have already done that using the above instructions. The rest of it is great. Don't worry about anything in the instructions in or past chapter 6.

If you have any other questions, feel free to post them.

---

### Post by euler_fan on 2007-08-19
Post script:

OSSEC-HIDS, rkhunter, and chkrootkit are good tools but should also be installed from source. Their websites have okay instructions if you want help there are some good howtos floating around for which are a little dated.

But it's up to you. The more paranoid you are the more time you should spend installing the latest security software from source. Without a volatile repo for Ubuntu anything in the repos gets outdated pretty quickly.

---

### Post by Akuma Shiro on 2007-08-19
> **euler_fan said:**
> Uninstall it. The best way to do ClamAV is from source. The software is well documented but I'm going to change the basic instructions some for extra security.

Go to add/remove applications and get the GPG program for your windows manager. I use Seahorse which works great for Gnome, but there is another one for KDE. They're under Accessories. You need this to verify the cryptographic signature files you are going to be working with.

get into the command line and do as follows:

```
wget http://freshmeat.net/redir/clamav/29355/url_tgz/clamav-0.91.1.tar.gz

wget http://downloads.sourceforge.net/clamav/clamav-0.91.1.tar.gz.sig

wget http://www.clamav.net/gpg/tkojm.gpg

gpg --import tkojm.gpg

gpg --verify clamav-X.XX.tar.gz.sig
```

replace the X.XX with the version number--0.91.1

IF upon completion of the last command the output indicates the signature, then and ONLY THEN will you continue with these instructions. If you do not get a good signature file, go into your home folder, delete the file you just downloaded, and start over again.

Should you get the response you are looking for, proceed as follows:

Download the install instructions from [here]("http://www.clamav.net/doc/latest/clamdoc.pdf") and follow the directions. Any terminal command that starts with a $ put in as seen. Anything following a # you need to use sudo for.

The instructions are very good, just do section 3.3 before section 3.2. Where it says to unpack the package, you have already done that using the above instructions. The rest of it is great. Don't worry about anything in the instructions in or past chapter 6.

If you have any other questions, feel free to post them.

It looked like all was going well untill...

```
troy@navi1L:~$ gpg --import tkojm.gpg
gpg: directory `/home/troy/.gnupg' created
gpg: can't open `/gnupg/options.skel': No such file or directory
gpg: keyring `/home/troy/.gnupg/secring.gpg' created
gpg: keyring `/home/troy/.gnupg/pubring.gpg' created
gpg: /home/troy/.gnupg/trustdb.gpg: trustdb created
gpg: key 985A444B: public key "Tomasz Kojm <tkojm@clamav.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
gpg: no ultimately trusted keys found
```

Is this what you meant when you said a good signature file?

---

### Post by Akuma Shiro on 2007-08-19
I meant not a good signature file?

---

### Post by euler_fan on 2007-08-19
Nope. Keep going. I think you're fine since the key file was successfully imported. If you go under Accessories and open "Passwords and Encryption Keys" (the name of the icon for Seahorse) and look under "Other Collected Keys" you should see one there. If not, post back.

The code with the "--verify" option is the one where you check the signature.

---

### Post by Akuma Shiro on 2007-08-19
```
troy@navi1L:~$ gpg --verify clamav-0.91.1.tar.gz.sig
gpg: Signature made Mon 16 Jul 2007 04:59:38 PM EDT using DSA key ID 985A444B
gpg: Good signature from "Tomasz Kojm <tkojm@clamav.net>"
gpg:                 aka "Tomasz Kojm <tk@lodz.tpnet.pl>"
gpg:                 aka "Tomasz Kojm <zolw@konarski.edu.pl>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0DCA 5A08 407D 5288 279D  B434 5482 2DC8 985A 444B
troy@navi1L:~$ 
```

Hardware im good with, but programs are my weakness... what does this mean?

---

### Post by euler_fan on 2007-08-19
> **Akuma Shiro said:**
> ```
troy@navi1L:~$ gpg --verify clamav-0.91.1.tar.gz.sig
gpg: Signature made Mon 16 Jul 2007 04:59:38 PM EDT using DSA key ID 985A444B
gpg: Good signature from "Tomasz Kojm <tkojm@clamav.net>"
gpg:                 aka "Tomasz Kojm <tk@lodz.tpnet.pl>"
gpg:                 aka "Tomasz Kojm <zolw@konarski.edu.pl>"
gpg: WARNING: This key is not certified with a trusted signature!
gpg:          There is no indication that the signature belongs to the owner.
Primary key fingerprint: 0DCA 5A08 407D 5288 279D  B434 5482 2DC8 985A 444B
troy@navi1L:~$ 
```

Hardware im good with, but programs are my weakness... what does this mean?

There's the long story and the short story. For the long story read up on GnuPG, public key encryption, and digital signatures. The GnuPG people have a very nice, in depth guide and Wikipedia, like usual, has a nice if occasionally technical summary.

The short version is that someone named Tomasz Kojm (one of the top ClamAV developers, actually) whom you don't know (I'm guessing) and don't trust (since you don't know him) signed the .tar.gz archive you downloaded which contains the source for ClamAV and said source has not been tampered with.

Of course, since you don't know him or anyone who knows him enough to vouch for him (loosely speaking), you still have to take a certain amount on faith. 

You can start the install part of this thing now.

---

