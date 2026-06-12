---
title: "Monodevelop Gutsy installation"
date: 2007-10-30
forum: Absolute Beginner Talk
---

### Post by cwmoser on 2007-10-30
Looking for advice on how to install the latest version of MonoDevelop.

The  MonoDevelop website is [www.mondevelop.com](www.mondevelop.com) and they have only a Source Code tarball or an RPM  package.  

If I select the Source Code tarball, I'll have to deal with compiling the package - and all the problems of finding all the libraries and dependencies.  If I select the RPM package, will alien properly convert the package?

Ubuntu repositories will install v0.14 but the latest version is v0.16.

Anyone have any suggestions on the proper way to install MonoDevelop on Ubuntu Gutsy?

Thanks

Carl

---

### Post by Sirron on 2007-10-31
GetDeb.net has it at: [http://www.getdeb.net/app.php?name=MonoDevelop](http://www.getdeb.net/app.php?name=MonoDevelop) in debian packages

0.16 is officially a beta, but I'm still finding it very unstable, please post your experience with it so I can see if it's just my computer acting up ^^

---

### Post by cwmoser on 2007-11-02
I had MonoDevelop v0.15 working just fine under Feisty.

Under Gutsy, neither v0.15 or v0.16 is usable.
When you click on MainWindow.cs, the MonoDevelop IDE crashes.

Carl

---

### Post by Sirron on 2007-11-04
I expect the package builders aren't aware of all the dependencies. In the ubuntu repos, there are a lot of packages relating to mono, and after installing some (not sure which, I just did as many as sounded useful ^^), I was able to make a simple form. So mono must be expecting to find things that just aren't there right?

I think there's supposed to be a beta launched before the new year, so I'll probably just leave it till then.

---

### Post by cwmoser on 2007-11-04
> **Sirron said:**
> I expect the package builders aren't aware of all the dependencies. In the ubuntu repos, there are a lot of packages relating to mono, and after installing some (not sure which, I just did as many as sounded useful ^^), I was able to make a simple form. So mono must be expecting to find things that just aren't there right?

I think there's supposed to be a beta launched before the new year, so I'll probably just leave it till then.

Thanks for the hint.  I'm concurring with you and going to just drop MonoDevelop until these bugs get attention.

Carl

---

### Post by cwmoser on 2007-11-06
Finally.  Monodevelop developers fixed the problem getting Monodevelop to work with Gutsy.

monodevelop_0.16-1~getdeb1_all.rpm DOES NOT WORK.

To get Monodevelop to work, you need the monodevelop-0.17-0.novell.noarch.rpm file.

Convert it to .deb file format via:

$  alien  monodevelop-0.17-0.novell.noarch.rpm


Carl

---

### Post by rdoolen on 2007-11-06
When I used:

alien monodevelop-0.17-0.novell.noarch.rpm

I got:

Warning: Skipping conversion of scripts in package monodevelop: postinst postrm
Warning: Use the --scripts parameter to include the scripts.

But it generated a deb, did you include the srcipts? or just use the deb without it?

---

### Post by cwmoser on 2007-11-06
I think you are right -- should include the --scripts parameter:

$ sudo alien --scripts mono*17*.rpm
monodevelop_0.17-1_all.deb generated

$ 


Carl

---

### Post by rdoolen on 2007-11-06
Well, I tried both with and without scipts, and I get a fireworks display of errors-- more pop-ups the a porn site, either way.

Did you do anything other than convert the rpm to a deb and install the deb? How did you install the deb? I used Gdebi.

I may try from source later as well.

---

### Post by cwmoser on 2007-11-07
Hmmm.  After using alien to convert the file to .deb format, I just right clicked on it via nautilus file browser and selected the GDebi Installer.

Maybe you got the wrong file.  The files and file size I have are:

monodevelop-0.17-0.novel.noarch.rpm    3,735,587
monodevelop_0.17-1_all.deb   3,920,774

I downloaded the rpm file from here:
[http://www.monodevelop.com/Download](http://www.monodevelop.com/Download)


Carl



> **rdoolen said:**
> Well, I tried both with and without scipts, and I get a fireworks display of errors-- more pop-ups the a porn site, either way.

Did you do anything other than convert the rpm to a deb and install the deb? How did you install the deb? I used Gdebi.

I may try from source later as well.

---

### Post by rdoolen on 2007-11-07
Sorry,  I thought I posted this yesterday, I must have written it but never posted it.

At any rate, I had success. All I had to do was delete the Monodevelop and Stetic directories in my ~/.config. Then everything worked just as you desribed.

Thanks for your help!!!

---

### Post by motters on 2007-11-07
At last I'm back in business with version 0.17 on Gutsy !

For anyone else who has been having the same troubles this is what I did:

1.  Removed existing 0.16 monodevelop installation using synaptic package manager
2.  Deleted monodevelop and stetic directories from the.config hidden folder
3.  sudo aptitude update && sudo aptitude install alien
4.  Download the 0.17 rpm from [http://www.monodevelop.com/Download](http://www.monodevelop.com/Download)
5.  sudo alien --scripts mono*17*.rpm
6.  Installed the deb file which is created

---

### Post by rdoolen on 2007-11-08
An additional observation, you may notice quite a few packages in the "auto removable" section in synaptic. These are needed for monodevelop, so don't remove them. I think they only appear this way if they were originally installed with monodevelop 0.1X that is remaoved in step 1 above.

I actually removed them to confirm they were needed. Then I reinstalled them on their own, and they are no longer in the auto removable section. 

At any rate, I am glad to be back in buisness.

---

### Post by pkid on 2007-12-03
Tried this and within 5 minutes I was running the latest version of MonoDevelop.  You guys rock.  Thanks again :guitar:

---

### Post by Gino Chen Hsiang-Jan on 2007-12-05
[B]Hi,
I installed Mono and MonoDevelop 0.17 using generic installer ( [ftp://www.go-mono.com/archive/1.2.5.1/linux-installer/3/mono-1.2.5.1_3-installer.bin](ftp://www.go-mono.com/archive/1.2.5.1/linux-installer/3/mono-1.2.5.1_3-installer.bin) ) and erased ~/.config/{MonoDevelop,stetic}. MonoDevelp are running correctly.
[/B]

---

### Post by rdoolen on 2007-12-05
Just an FYI, an update for many of the mono packages was just posted. (Dec 4, 2007). I installed them and everything is OK, at least initially.

---

### Post by Tommy.86 on 2008-02-12
> **Gino Chen Hsiang-Jan said:**
> [B]Hi,
I installed Mono and MonoDevelop 0.17 using generic installer ( [ftp://www.go-mono.com/archive/1.2.5.1/linux-installer/3/mono-1.2.5.1_3-installer.bin](ftp://www.go-mono.com/archive/1.2.5.1/linux-installer/3/mono-1.2.5.1_3-installer.bin) ) and erased ~/.config/{MonoDevelop,stetic}. MonoDevelp are running correctly.
[/B]


Hi, im begginer, i wanted to install monodevelop 0.17. i downloaded mono-1.2.5.1_3-installer.bin from ftp
i wrote to console:

$  chmod u+x mono-1.2.5.1_3-installer.bin
$  ./mono-1.2.5.1_3-installer.bin

and in 100%  it wrote:

Error executing post installation script
/opt/mono-1.2.5.1/bin/.installer_post_libscan
\/opt/mono-1.2.5.1/bin/.installer_post_libscan: 9: Syntax error: "(" unexpected

Can u help me? I don't know what wrong is. :(

---

