---
title: "[SOLVED] Synaptic Error on Fiesty"
date: 2007-10-19
forum: Absolute Beginner Talk
---

### Post by raja.aydina on 2007-10-19
I was going through a website and was following commands, the next thing I know when I go into synaptic, I get the following error right at start up and I can't get into synaptic.   I would really appreciate any help

E: Type '<!DOCTYPE' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

raja aydina

---

### Post by forestpixie on 2007-10-19
post your sources.list here - you've got a problem with it, easily fixed I'd imagine - there's a problem with the first line

```
cat /etc/apt/sources.list
```

---

### Post by RomeReactor on 2007-10-19
Hi.You have an error in the medibuntu.list file.  Please post the output of running the following command on the terminal (Applications->Accessories->Terminal):
```
cat /etc/apt/sources.list.d/medibuntu.list
```

---

### Post by forestpixie on 2007-10-19
whoops - yea that list not the one I said :oops:

---

### Post by raja.aydina on 2007-10-19
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) feisty-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) feisty-updates restricted main multiverse universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse
deb [http://ntfs-3g.sitesweetsite.info/ubuntu/](http://ntfs-3g.sitesweetsite.info/ubuntu/) edgy main main-all
deb [http://flomertens.keo.in/ubuntu/](http://flomertens.keo.in/ubuntu/) edgy main main-all

---

### Post by forestpixie on 2007-10-19
you need to do the one romereactor said :)

---

### Post by raja.aydina on 2007-10-19
thanks for quick replies, heres source after:

 cat /etc/apt/sources.list.d/medibuntu.list


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
                </html>

---

### Post by raja.aydina on 2007-10-19
i guess i put in a website instead of a repository, how do i fix it?
thanks.

---

### Post by forestpixie on 2007-10-19
That's not going to work :)

I would rename that file and get medibuntu this way, then if all ok delete the old file

```
 sudo mv  /etc/apt/sources.list.d/medibuntu.list /etc/apt/sources.list.d/medibuntu.list.bak
```

```
sudo wget http://www.medibuntu.org/sources.list.d/feisty.list -O /etc/apt/sources.list.d/medibuntu.list
```

```
wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update
```

if all is well delete the backed up file 

```
sudo rm /etc/apt/sources.list.d/medibuntu.list.bak
```

---

### Post by RomeReactor on 2007-10-19
Opne the Medibuntu file in Gedit:
```
gksudo gedit /etc/apt/sources.list.d/medibuntu.list
```
You need to delete the contents of the entire file (NOTE: not the file itself) and add the folowing:
```
## Medibuntu - Ubuntu 7.04 "feisty fawn"
## Please report any bug on https://bugs.launchpad.net/medibuntu/
deb http://packages.medibuntu.org/ feisty free non-free
#deb-src http://packages.medibuntu.org/ feisty free non-free
```
Now save the file, close the text editor

I'm on Gutsy now, so I just changed "gutsy" for "feisty". It should work though.

**EDIT**: Or just do what forestpixie says; it's easier :D

---

### Post by raja.aydina on 2007-10-19
thanks.. synaptic works again!!!

---

### Post by raja.aydina on 2007-10-19
thanks guys.. really appreciate it.. synaptic works again!!!

---

### Post by forestpixie on 2007-10-19
great - can you mark thread solved :)

---

### Post by jureuser on 2007-10-28
Hi!
This the first time I'm using ubuntu (or any other Linux application). I have a similar problem as written above:

E: Type '--10:37:20--' is not known on line 1 in source list /etc/apt/sources.list.d/medibuntu.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

I believe at the moment I was running the commands, the internet connection was down (I didn't notice that). When I use   _cat /etc/apt/sources.list.d/medibuntu.list_, I get


--10:37:20--  [http://www.medibuntu.org/sources.list.d/gutsy.list](http://www.medibuntu.org/sources.list.d/gutsy.list)
           => `gutsy.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... failed: Name or service not known.

Can you help me with this?

---

