---
title: "I buggered by OS, but I have details how I did it within..."
date: 2008-02-14
forum: Absolute Beginner Talk
---

### Post by h-town on 2008-02-14
Ok, I did a fresh install of ubuntu, and I consulted this guide:

[http://linuxondesktop.blogspot.com/search?q=top+13+things+to+do+after](http://linuxondesktop.blogspot.com/search?q=top+13+things+to+do+after)

And I was in the first section of the guide for updating my repositories and I entered the code. Didn't seem to work after entering in both pieces of code. So I said "whatever" to that and tried to open up synaptic package manager.. HOWEVER now I get this error message:

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.


That's when I noticed that the guide was for a previous version of Ubuntu.. I messed up again. 

Is there a way to restore/repair/reinstall/etc so ubuntu works.

---

### Post by jan quark on 2008-02-14
please run this command and post the output

```
cat /etc/apt/sources.list
```

---

### Post by h-town on 2008-02-14
I've also noticed a new orange icon with a star burst in the middle on the top of my screen and when I hold the pointer over it a message appears:

This usually means that your installed packages have unmet dependencies

And when I click it Update Manager pops open and a small box with a caution-y sort of icon is open and all I can do is close it, which closes Update Manager.

The plot thickens.... help me :confused:

---

### Post by h-town on 2008-02-14
# deb cdrom:[Ubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016)]/ gutsy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy universe
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy multiverse
deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse
# deb-src [http://ca.archive.ubuntu.com/ubuntu/](http://ca.archive.ubuntu.com/ubuntu/) gutsy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) gutsy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) gutsy-security multiverse

---

### Post by PeterJS on 2008-02-14
The (main) sources list should be fine. Looks like the error is in /etc/apt/sources.list.d/medibuntu.list, try
```

cat /etc/apt/sources.list.d/medibuntu.list

```

---

### Post by jan quark on 2008-02-14
> And I was in the first section of the guide for updating my repositories and I entered the code. Didn't seem to work after entering in both pieces of code. So I said "whatever" to that and tried to open up synaptic package manager.. HOWEVER now I get this error message:

what was this code :confused:

---

### Post by h-town on 2008-02-14
> **PeterJS said:**
> The (main) sources list should be fine. Looks like the error is in /etc/apt/sources.list.d/medibuntu.list, try
```

cat /etc/apt/sources.list.d/medibuntu.list

```
 
Here's what I got

```
harrison@machine:~$ cat /etc/apt/sources.list.d/medibuntu.list
  <!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "DTD/xhtml1-strict.dtd">
                <html xmlns="http://www.w3.org/1999/xhtml" xml:lang="en" lang="en">
                <head>
                    <title>Medibuntu :: Multimedia, Entertainment &amp; Distractions In Ubuntu</title>
                    <meta http-equiv="Content-Type" content="text/xhtml+xml; charset=utf-8" />
                    <link rel="stylesheet" href="medibuntu.css" type="text/css" />
                </head>
                    <body>
                        <div id="header">
                            <h1><span class="hidden">Medibuntu<br />Multimedia, Entertainment &amp; Distractions In Ubuntu</span></h1>
                        </div>
                        <ul id="menu"><li><a href="index.php">Presentation</a></li>
                        <li><a href="http://help.ubuntu.com/community/Medibuntu">Repository Howto</a></li>
                        <li><a href="packages.php">Packages</a></li>
                        <li><a href="contact.php">Contact us</a></li>
                                 </ul>
        <div id="page">
              <h2>Presentation</h2>
                                <p>
                                    <strong>
                                        Medibuntu (Multimedia, Entertainment &amp; Distractions In Ubuntu) is a repository of packages that cannot be included into the Ubuntu distribution for legal reasons (copyright, license, patent, etc).
                                    </strong>
                                </p>
                                <p>
                                    Medibuntu is a packaging project dedicated to distributing software that cannot be included in Ubuntu for various reasons, related to geographical variations in legislation regarding intellectual property, security and other issues:
                                </p>
                                <ul>
                                    <li>patentability of software, algorithms, formats and other abstract creation</li>
                                    <li>legal restrictions on freedom of speech or communication</li>
                                    <li>restrictions on the use of certain types of technical solution, such as cryptography</li>
                                    <li>legal restrictions on imports of software technology, requiring for example specific permissions</li>
                                    <li>etc.</li>
                                </ul>
                                <p>
                                    A lot of excellent <a href="http://www.fsf.org/licensing/essays/free-sw.html">free software</a> and non-free software is affected by such restriction somewhere in the world, thus preventing its inclusion into Ubuntu that, for economy and simplicity, are generally identical for all countries.
                                </p>
                                <p>
                                    We refuse to resign ourselves to abandoning software that may be legally useful somewhere, and we have chosen to provide it with professional quality packaging, easily usable within the context of Ubuntu.<br />
                                    This repository provides packages for Ubuntu distribution.
                                </p>
                                <p>
                                    It is your legal responsibility to make sure that the software you are installing can be legally used in your country and for your intended purpose.
                                </p>
                                        </div>
          <div id="paypal"><form action="https://www.paypal.com/cgi-bin/webscr" method="post">
<p>
<input type="hidden" name="cmd" value="_xclick" />
<input type="hidden" name="business" value="maxenced@gmail.com" />
<input type="hidden" name="item_name" value="Medibuntu" />
<input type="hidden" name="no_shipping" value="0" />
<input type="hidden" name="no_note" value="1" />
<input type="hidden" name="currency_code" value="EUR" />
<input type="hidden" name="tax" value="0" />
<input type="hidden" name="bn" value="PP-DonationsBF" />
<input type="image" src="https://www.paypal.com/en_US/i/btn/x-click-but04.gif" name="submit" alt="Effectuez vos paiements via PayPal : une solution rapide, gratuite et sécurisée" />
<img alt="" src="https://www.paypal.com/en_US/i/scr/pixel.gif" width="1" height="1" />
</p>
</form>
          </div>
                        <div id="footer">:: designed by <a href="http://www.most-enchained.com">_Enchained</a> - logo by <a href="http://www.racoon97.net">racoon97</a> - Domain by <a href="http://flosoft.biz">Flosoft</a>  - Managed by <a href="http://www.dunnewind.net">Sp4rKy</a> ::          </div>
<!-- phpmyvisites -->
<a href="http://www.phpmyvisites.us/" title="phpMyVisites | Open source web analytics"
onclick="window.open(this.href);return(false);"><script type="text/javascript">
<!--
var a_vars = Array();
var pagename='';

var phpmyvisitesSite = 2;
var phpmyvisitesURL = "http://stats.dunnewind.net/phpmyvisites.php";
//-->
</script>
<script language="javascript" src="http://stats.dunnewind.net/phpmyvisites.js" type="text/javascript"></script>
<object><noscript><p>phpMyVisites | Open source web analytics
<img src="http://stats.dunnewind.net/phpmyvisites.php" alt="Statistics" style="border:0" />
</p></noscript></object></a>
<!-- /phpmyvisites --> 
    </body>
                </html>harrison@machine:~$ 


```

---

### Post by h-town on 2008-02-14
> **jan quark said:**
> what was this code :confused:

These two little demons:

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - 
sudo wget http://medibuntu.sos-sts.com/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by PeterJS on 2008-02-14
Looks like you got the wrong page piped in there that's a web page, look at the format of your main source list, and the medibuntu one. It's in the wrong format, try deleting /etc/apt/sources.list.d/medibuntu.list. The new medibuntu instructions can be found here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)

---

### Post by h-town on 2008-02-14
> **PeterJS said:**
> Looks like you got the wrong page piped in there that's a web page, look at the format of your main source list, and the medibuntu one. It's in the wrong format, try deleting /etc/apt/sources.list.d/medibuntu.list. The new medibuntu instructions can be found here:
[https://help.ubuntu.com/community/Medibuntu](https://help.ubuntu.com/community/Medibuntu)


Here's what happened:

```
harrison@machine:/etc/apt/sources.list.d$ rm medibuntu.list
rm: remove write-protected regular file `medibuntu.list'? y
rm: cannot remove `medibuntu.list': Permission denied
harrison@machine:/etc/apt/sources.list.d$ 

```

:confused:


There is also a medibuntu.list.save file in that directory as well.

---

### Post by jan quark on 2008-02-14
```
sudo cp /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list_backup
```
```
sudo rm /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by PeterJS on 2008-02-14
For more on permissions and sudo see:
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)

---

### Post by h-town on 2008-02-14
All right!! You fixed it dude. Thanks a lot. I was so annoyed with myself. Thanks to both of you for taking the time to help a stranger. :KS

---

### Post by jan quark on 2008-02-14
hey you are welcome

not for nothing we are both in the beginners team :lolflag:

mark this thread as solved please see signature

thank you and a happy linux experience

---

