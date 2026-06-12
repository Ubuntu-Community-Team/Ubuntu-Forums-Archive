---
title: "Automatix no longer installs Adobe Reader"
date: 2007-03-29
forum: Absolute Beginner Talk
---

### Post by marianlibrarian on 2007-03-29
I just downloaded Automatix2 on a Dapper Drake Computer and found that it no longer will install Adobe Reader. 

Can someone check into this? I have used Automatix to install Adobe Reader, Flash, and several other items on 6 new Ubuntu machines. Now the only thing it still installs is - Flash. I need to have Adobe Reader. These are public access machines in a public library. 

**What has happened to Automatix??? It went down about a week ago for a long time but when it came back, it is a watered down version. Very little of the applications on it are ones that I would use.**

I dread asking this due to the remarks I have seen in other posts....

But, is there an alternative to automatix? I know about the Easy Ubuntu but this machine already has Ubuntu regular installed. I tried installing adobe reader sometime ago without automatix and it didn't turn out so well. 

I can use the command line if I have to, if someone will share the lines of code to get adobe reader installed.

---

### Post by mcduck on 2007-03-29
What's wrong with using Evince, the reader that comes with Ubuntu? It's much lighter and faster than Acrobat has ever been, and works perfectly reading PDF files..

---

### Post by jem7v on 2007-03-29
EasyUbuntu isn't a different version of Ubuntu - it's a program like Automatix... it just doesn't do as many things as Automatix, the last time I checked.

As for Adobe Acrobat, just go to Applications>Add/Remove. It's in there under "Adobe Reader."  All you have to do is check it off and click Apply.

Did you know, though, that your default install already includes Evince (aka "Document Reader") and can view .pdfs without the actual Adobe program?

---

### Post by marianlibrarian on 2007-03-29
Well, blow me down! I feel like a one legged man in a butt kicking contest. 

You are right. I didn't install adobe reader on this machine and when I opened up a pdf - there it was. Opened right up. 

I have only been using Ubuntu or any kind of Linux since February - this year :) I have a lot to learn.

Thanks for the input! Automatix redid their website. It looks nice but it sure was slow.

---

### Post by compiledkernel on 2007-03-31
Automatix is unsupported software by the community. These forums do not support it either. If you have further difficulties with Automatix, you should refer back to their forums at [www.getautomatix.com](www.getautomatix.com) for further help.

Let me firmly reiterate that Automatix is just as it is --

"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu."

---

### Post by penvzila on 2007-04-08
> **mcduck said:**
> What's wrong with using Evince, the reader that comes with Ubuntu? It's much lighter and faster than Acrobat has ever been, and works perfectly reading PDF files..

It does not work perfectly at all.  For example, it messes up the bookmarks I created in Acrobat.  In Acrobat reader, the bookmarks point to the correct pages.  And while it is fast, the rendering, especially of images, is pretty horrible compared to acrobat.  For me, Evince is totally unusable.

---

### Post by richbarna on 2007-04-10
> **compiledkernel said:**
> 
"automatix is a script that tries to install some software, and often
fails and breaks systems. We don't provide support for it, and we strongly
discourage its use. Problems caused by Automatix are often hard to track
and solve, and it might sometimes be easier to !install a fresh copy of
Ubuntu.":confused:

That's very unfair when the developers don't actually use these forums, they can't post and defend their app or answer doubts. The new users here only have your word to go on. As you are a staff member, they are very likely to believe everything you write.
Now read what the developers and users have to say about this quote. It's only fair to hear both sides of every story. :)

[What the developers and users say about certain misleading quotes]("http://www.modfree.org/index.php?topic=580.0")

---

### Post by KiwiNZ on 2007-04-11
Automatix is an independant project to assist users install additional applications. Like any independent project there will be risks with its use.

Many users have used it with out issue. Others have used it and had problems. That is something that occurs and is not only restricted to Automatix , any software can cause issues.

If you want to use Automatix I strongly suggest you read the Automatix Support forum that the creator has established. 
If you have any issues with it you should also refer to that support forum , that is where the expertise is .

After all it is your PC , you are free to use on it what you wish , that is one of joys of Open Source , freedom.

Ubuntu Forums does not provide support for Automatix

---

### Post by aysiu on 2007-04-11
The Medibuntu repositories have *acroread* in them:
[http://medibuntu.sos-sts.com/packages.php](http://medibuntu.sos-sts.com/packages.php)

---

### Post by mstlyevil on 2007-04-11
We got dugg and it crippled us until a ram upgrade yesterday. We host a more recent version of acrobat reader on our server so that is why it failed to install. The RAM upgrade has fixed this problem.

For Automatix support go to [www.getautomatix.com](www.getautomatix.com).

---

### Post by marianlibrarian on 2007-11-02
I am back. First of all - Evince - is NOT an alternative to Adobe Reader. With that said, I NEED Adobe Reader and Flash. I have patrons and my staff who need the real Adobe Reader. I have a report that prints my book labels as a pdf. When it opens in that Evince thing, it is not formatted properly and does not print on the page correctly.

I have looked all over the place for a simple way to install these programs. I have found everything but --- simple.

I have found references to "backports repository" and when I tried that It gave me a "404 not found" error. 

If someone knows where the instructions are to install both Adobe REader and Adobe Flash - please please please - post it here.

Thanks.

---

### Post by Maestro23 on 2007-11-02
Make sure you have all your sources enabled, as well as adding the Medibuntu: [https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29](https://help.ubuntu.com/community/Medibuntu?highlight=%28Medibuntu%29)

Once that is done:

> sudo apt-get install acroread

sudo apt-get install flashplugin-nonfree

---

### Post by marianlibrarian on 2007-11-02
I installed the medi thing repository and did not receive any errors. But when I put in the two commands given above, I get the following error on both:

E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Any ideas?

Thanks

---

### Post by compiledkernel on 2007-11-02
Make sure no other dpkg-esque processes are running ie. Update-manager, Synaptic, apt-get, aptitude, adept, etc.

---

### Post by marianlibrarian on 2007-11-02
I have been consulting a book called "Beginning Ubuntu Linux" by Keir Thomas in hopes that I would not have to ask to many stewpid questions. There is a chapter on "Installing Software" that sort of describes things but doesn't go into detail if there is a problem.

So, how do I tell if these processes are running? And if they are, how do I stop them?

Thanks

---

### Post by aysiu on 2007-11-02
You would know if Update Manager, Synaptic Package Manager, or Adept was running. Each of those processes is a graphical window that appears.

Just close the window before you run any *apt-get* command.

---

### Post by marianlibrarian on 2007-11-02
A clue to the clueless: I realized that while I was studying my book that I had the synaptic window --- open. Ah Ha. When I closed it, that error went away but now I have a new one:

librarian@ubuntuserver:~$  sudo apt-get install acroread
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread
librarian@ubuntuserver:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree

So I am thinking that there was a problem when I installed the Medi repository thing and I didn't see it?

Here is the whole thing from getting the medibuntu list to "can't find package" error.

> librarian@ubuntuserver:~$ sudo wget [http://www.medibuntu.org/sources.list.d/dapp](http://www.medibuntu.org/sources.list.d/dapp) er.list -O /etc/apt/sources.list.d/medibuntu.list
Password:
--10:16:38--  [http://www.medibuntu.org/sources.list.d/dapper.list](http://www.medibuntu.org/sources.list.d/dapper.list)
           => `/etc/apt/sources.list.d/medibuntu.list'
Resolving [www.medibuntu.org](www.medibuntu.org)... 87.98.242.10
Connecting to www.medibuntu.org|87.98.242.10|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 229 [text/plain]

100%[====================================>] 229           --.--K/s

10:16:43 (21.84 MB/s) - `/etc/apt/sources.list.d/medibuntu.list' saved [229/229]

librarian@ubuntuserver:~$ sudo apt-get install acroread
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavail able)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another proc ess using it?
librarian@ubuntuserver:~$ sudo apt-get install flashplugin-nonfree
E: Could not get lock /var/lib/dpkg/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?
librarian@ubuntuserver:~$  sudo apt-get install acroread
Password:
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread
librarian@ubuntuserver:~$ sudo apt-get install flashplugin-nonfree
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package flashplugin-nonfree
librarian@ubuntuserver:~$

---

### Post by aysiu on 2007-11-02
After you add a new source (like the Medibuntu one), you have to let Ubuntu check to see what new software is available in that source.

The command to check what's now available is *sudo apt-get update*

So it would be ```
sudo apt-get update
sudo apt-get install acroread acroread-plugins
``` For Flash, before you install it, go to System > Administration > Software Sources and make sure Multiverse is checked off (actually, go ahead and check them all off, except the CD-ROM source). Then you'll be prompted to "Reload" your information (same as *sudo apt-get update*). Then you can install Flash.

More details on that here (with screenshots):
[http://www.psychocats.net/ubuntu/flash](http://www.psychocats.net/ubuntu/flash)

---

### Post by compiledkernel on 2007-11-02
first off, you need to run apt-get update after you add the repo, but before you do even that you need to make sure you have the proper gpg key. 

To do both do this. 

wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update

---

### Post by aysiu on 2007-11-02
No offense to Keir Thomas, but I think these links would be better for learning how to install software.

The first link helps you understand the principle of software installation and gives a brief overview of how it works:
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

The second link shows you how to install software without using the terminal (it includes a lot of screenshots):
[http://www.monkeyblog.org/ubuntu/installing](http://www.monkeyblog.org/ubuntu/installing)

---

### Post by marianlibrarian on 2007-11-02
I did that and all kinds of text happened. When it said "Done", I re-entered the command to install the adobe reader application and I got the same error again. Here is the text from the command you gave me above to the error message I recieved with the adobe reader application:

> librarian@ubuntuserver:~$ wget -q [http://packages.medibuntu.org/medibuntu-key.gpg](http://packages.medibuntu.org/medibuntu-key.gpg) -O- | sudo apt-key add - && sudo apt-get update
Password:
Sorry, try again.
Password:
OK
Get:1 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release.gpg [189B]
Get:2 [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release.gpg [191B]
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates Release
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper/restricted Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Packages
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/main Sources
Hit [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) dapper-updates/restricted Sources
Get:3 [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release.gpg [191B]
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security Release
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Packages
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/main Sources
Hit [http://security.ubuntu.com](http://security.ubuntu.com) dapper-security/restricted Sources
Get:4 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release.gpg [189B]
Get:5 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper Release [2188B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages
Get:6 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/free Packages [1847B]
Get:7 [http://packages.medibuntu.org](http://packages.medibuntu.org) dapper/non-free Packages [1568B]
Fetched 5795B in 13s (437B/s)
Reading package lists... Done
librarian@ubuntuserver:~$ sudo apt-get install acroread
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package acroread
librarian@ubuntuserver:~$


---

### Post by aysiu on 2007-11-02
That's weird. Maybe because you're using Dapper and not Feisty or Gutsy?

Let's try something else then.

Download these files to your desktop:
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.1-0medibuntu3_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_8.1.1-0medibuntu3_i386.deb)
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.1-0medibuntu3_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_8.1.1-0medibuntu3_i386.deb)
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.1-0medibuntu3_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_8.1.1-0medibuntu3_i386.deb)

Then paste these two commands into the terminal: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by marianlibrarian on 2007-11-02
I downloaded the three files to my desktop and then used the commands as stated above. I copied and pasted below the result:

> librarian@ubuntuserver:~$ cd ~/Desktop
librarian@ubuntuserver:~/Desktop$ sudo dpkg -i *.deb
Password:
Selecting previously deselected package acroread.
(Reading database ... 92184 files and directories currently installed.)
Unpacking acroread (from acroread_8.1.1-0medibuntu3_i386.deb) ...
Selecting previously deselected package acroread-escript.
Unpacking acroread-escript (from acroread-escript_8.1.1-0medibuntu3_i386.deb) ...
Selecting previously deselected package acroread-plugins.
Unpacking acroread-plugins (from acroread-plugins_8.1.1-0medibuntu3_i386.deb) ...
dpkg: dependency problems prevent configuration of acroread:
 acroread depends on libatk1.0-0 (>= 1.13.2); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 acroread depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 acroread depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 acroread depends on libgtk2.0-0 (>= 2.12.0); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 acroread depends on libpango1.0-0 (>= 1.18.2); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
 acroread depends on zlib1g (>= 1:1.2.3.3.dfsg-1); however:
  Version of zlib1g on system is 1:1.2.3-6ubuntu4.
dpkg: error processing acroread (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acroread-escript:
 acroread-escript depends on acroread; however:
  Package acroread is not configured yet.
 acroread-escript depends on libc6 (>= 2.6-1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 acroread-escript depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 acroread-escript depends on libglib2.0-0 (>= 2.14.0); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 acroread-escript depends on libgtk2.0-0 (>= 2.12.0); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
dpkg: error processing acroread-escript (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acroread-plugins:
 acroread-plugins depends on acroread (= 8.1.1-0medibuntu3); however:
  Package acroread is not configured yet.
 acroread-plugins depends on acroread-escript; however:
  Package acroread-escript is not configured yet.
dpkg: error processing acroread-plugins (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acroread
 acroread-escript
 acroread-plugins
librarian@ubuntuserver:~/Desktop$

Oh and thank you for helping me with this. Even if it isn't working like it should, I really appreciate your help.

---

### Post by aysiu on 2007-11-02
Hm. Maybe that version's too high for Dapper. Let's try this then...

Delete all those .deb files off your desktop.

Download these to your desktop instead:
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-escript_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb)
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread-plugins_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb)
[http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb](http://packages.medibuntu.org/pool/non-free/a/acroread/acroread_7.0.9-0.0.ubuntu0.7.04%2bmedibuntu2_i386.deb)

And then try those commands again: ```
cd ~/Desktop
sudo dpkg -i *.deb
```

---

### Post by stchman on 2007-11-02
Follow my procedure to install Adobe Acrobat 7 in Feisty or Gutsy.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Simple.

---

### Post by aysiu on 2007-11-02
> **stchman said:**
> Follow my procedure to install Adobe Acrobat 7 in Feisty or Gutsy.

[http://www.stchman.com/install_adobe.html](http://www.stchman.com/install_adobe.html)

Simple.
Except that marianlibrarian is using Dapper.

In fact, the procedures outllined in that link are precisely what the OP has tried, and it didn't work. Thanks, anyway, though.

---

### Post by marianlibrarian on 2007-11-02
I deleted the first three files and downloaded the second set and then used the command - sudo dpkg -1 *.deb   Following is the text result:

> librarian@ubuntuserver:~/Desktop$ sudo dpkg -i *.deb
Password:
(Reading database ... 92723 files and directories currently installed.)
Preparing to replace acroread 8.1.1-0medibuntu3 (using acroread_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb) ...
Unpacking replacement acroread ...
Preparing to replace acroread-escript 8.1.1-0medibuntu3 (using acroread-escript_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb) ...
Unpacking replacement acroread-escript ...
Preparing to replace acroread-plugins 8.1.1-0medibuntu3 (using acroread-plugins_7.0.9-0.0.ubuntu0.7.04+medibuntu2_i386.deb) ...
Unpacking replacement acroread-plugins ...
dpkg: dependency problems prevent configuration of acroread:
 acroread depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 acroread depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 acroread depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 acroread depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 acroread depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
dpkg: error processing acroread (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acroread-escript:
 acroread-escript depends on libatk1.0-0 (>= 1.13.1); however:
  Version of libatk1.0-0 on system is 1.11.4-0ubuntu1.
 acroread-escript depends on libc6 (>= 2.5-0ubuntu1); however:
  Version of libc6 on system is 2.3.6-0ubuntu20.5.
 acroread-escript depends on libfontconfig1 (>= 2.4.0); however:
  Version of libfontconfig1 on system is 2.3.2-1.1ubuntu12.
 acroread-escript depends on libglib2.0-0 (>= 2.12.9); however:
  Version of libglib2.0-0 on system is 2.10.3-0ubuntu1.
 acroread-escript depends on libgtk2.0-0 (>= 2.10.3); however:
  Version of libgtk2.0-0 on system is 2.8.20-0ubuntu1.1.
 acroread-escript depends on libpango1.0-0 (>= 1.16.2); however:
  Version of libpango1.0-0 on system is 1.12.3-0ubuntu3.
dpkg: error processing acroread-escript (--install):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of acroread-plugins:
 acroread-plugins depends on acroread (= 7.0.9-0.0.ubuntu0.7.04+medibuntu2); however:
  Package acroread is not configured yet.
 acroread-plugins depends on acroread-escript; however:
  Package acroread-escript is not configured yet.
dpkg: error processing acroread-plugins (--install):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 acroread
 acroread-escript
 acroread-plugins
librarian@ubuntuserver:~/Desktop$

---

### Post by PmDematagoda on 2007-11-02
Why don't you download the .deb file off the Adobe web site found here:

[http://www.adobe.com/uk/products/acrobat/readstep2_allversions.html](http://www.adobe.com/uk/products/acrobat/readstep2_allversions.html)

and install it as normal.

---

### Post by marianlibrarian on 2007-11-02
>  		Why don't you download the .deb file off the Adobe web site found here:

[http://www.adobe.com/uk/products/acr...lversions.html]("http://www.adobe.com/uk/products/acrobat/readstep2_allversions.html")

and install it as normal.


Did that and the package installer said that:

[COLOR=Red][B]Error: Failed to satisfy all
dependencies (broken cache.)[/B][/COLOR]

---

### Post by PmDematagoda on 2007-11-02
It may be something wrong with apt-get, do:-
```

sudo apt-get check
```

and post what you get.

---

### Post by marianlibrarian on 2007-11-02
Here it is:

> librarian@ubuntuserver:~/Desktop$ sudo apt-get check
Password:
Reading package lists... Done
Building dependency tree... Done
You might want to run `apt-get -f install' to correct these.
The following packages have unmet dependencies:
  acroread: Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is installed
            Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed
            Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed
            Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed
            Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed
  acroread-escript: Depends: libatk1.0-0 (>= 1.13.1) but 1.11.4-0ubuntu1 is installed
                    Depends: libc6 (>= 2.5-0ubuntu1) but 2.3.6-0ubuntu20.5 is installed
                    Depends: libfontconfig1 (>= 2.4.0) but 2.3.2-1.1ubuntu12 is installed
                    Depends: libglib2.0-0 (>= 2.12.9) but 2.10.3-0ubuntu1 is installed
                    Depends: libgtk2.0-0 (>= 2.10.3) but 2.8.20-0ubuntu1.1 is installed
                    Depends: libpango1.0-0 (>= 1.16.2) but 1.12.3-0ubuntu3 is installed
E: Unmet dependencies. Try using -f.
librarian@ubuntuserver:~/Desktop$

---

### Post by compiledkernel on 2007-11-02
Then assume 

sudo apt-get install -f 

and post the output that gives you.

---

### Post by marianlibrarian on 2007-11-02
Here you go:

> librarian@ubuntuserver:~/Desktop$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree... Done
Correcting dependencies... Done
The following packages will be REMOVED:
  acroread acroread-escript acroread-plugins
0 upgraded, 0 newly installed, 3 to remove and 0 not upgraded.
3 not fully installed or removed.
Need to get 0B of archives.
After unpacking 111MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 92537 files and directories currently installed.)
Removing acroread-plugins ...
Removing acroread ...
Removing acroread-escript ...
librarian@ubuntuserver:~/Desktop$

I am assuming that this worked. Yippee 

Now I need to do Flash ----- but that can wait another day

THANK YOU for all your help!

---

### Post by PmDematagoda on 2007-11-02
Now try installing Acrobat Reader using the .deb you downloaded.

---

### Post by stchman on 2007-11-02
> **aysiu said:**
> Except that marianlibrarian is using Dapper.

In fact, the procedures outllined in that link are precisely what the OP has tried, and it didn't work. Thanks, anyway, though.

Dapper and Edgy already have Adobe Acrobat reader 7 in its repositories so the Medibuntu stuff is not necessary.

Dapper (multiverse)
Edgy (multiverse)

Make sure these repos are enabled in the software sources.

Dapper install
```
sudo aptitude update
sudo aptitude install acroread
```

Edgy
```

sudo apt-get update
sudo apt-get install acroread
```

When Feisty came out Ubuntu removed Acrobat from the repos.

---

### Post by marianlibrarian on 2007-11-02
I am a dork dork dork. I had to watch the front while my co-worker went to lunch and then I had to get a document notorized across the street and then there was a message that said:

Now try installing Acrobat Reader using the .deb you downloaded.

And I didn't see that part... so just a minute while I get that done. - thanks

Edit: Now try installing Acrobat Reader using the .deb you downloaded

You know what? I am so confused at this moment that I don't know how to "try installing Acrobat Reader using the .deb you downloaded." Can someone give me the line of code that will do this?  Unless it is: sudo aptitude install acroread or sudo apt-get install acroread. Those don't work. 

Edit Edit: Since only Mark for removal worked in synaptic list thing I just marked that and I give up even though I really really need this. I can't take this anymore. I still have one windows machine that has acrobat reader on it.

You know if you want more places like public libraries to use linux then finding a way to install something like adobe reader and flash that doesn't take so many hours and still doesn't work would be nice and I would say more nice things about how "easy?" ubuntu is.

I WANT MY AUTOMATIX BACK - AGHHHHHHHHHHHHHHHHHHHHHHHHHHH

---

### Post by aysiu on 2007-11-02
> **marianlibrarian said:**
> I am a dork dork dork. I had to watch the front while my co-worker went to lunch and then I had to get a document notorized across the street and then there was a message that said:

Now try installing Acrobat Reader using the .deb you downloaded.

And I didn't see that part... so just a minute while I get that done. - thanks
Go to System > Administration > Software Properties (or Software Sources--I forget what it's called).

Check off all the boxes (especially Multiverse) except the CD-ROM source.

It'll ask if you want to Reload. Say yes.

Then close that dialogue and go to Synaptic. Both *acroread* and *flashplugin-nonfree* should be available for installation.

I think the main problem here is that you're using Dapper and the people who are helping you are using Feisty or Gutsy (the more recent versions of Ubuntu).

---

### Post by compiledkernel on 2007-11-02
SideQuestion: assuming that you are using dapper, will they (your superiors) allow you to use Heron when its released (it being the next in the line of LTS releases)?

---

### Post by marianlibrarian on 2007-11-02
>  Check off all the boxes (especially Multiverse) except the CD-ROM source.

I found "Software Preferences" and I checked off (meaning I put a check mark in all the little boxes) ---- but there is no such thing as Multiverse and there is no such thing as CD-ROM source.

I have not hit the enter key yet. What will this DO???

---

### Post by marianlibrarian on 2007-11-02
okay i did that and when I hit close it said "did I want to reload" I said yes. and then it popped up a "Warning" window:

> W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/main Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_main_binary-i386_Packages)
W: Duplicate sources.list entry cdrom://Ubuntu 6.06.1 _Dapper Drake_ - Release i386 (20060807.1) dapper/restricted Packages (/var/lib/apt/lists/Ubuntu%206.06.1%20%5fDapper%20Drake%5f%20-%20Release%20i386%20(20060807.1)_dists_dapper_restricted_binary-i386_Packages)
:confused:

Edit: Oh and I went to synaptic and there is no acroread and there is no flash.  I have to give up and hope that I have not done some kind of damage to this computer with all the stuff I did here. It is closing time and I have anohter server to upgrade. It is Debian Sarge and doen'st need all adobe anything on it.

Thanks for your attention here. No other place anywhere has this kind of service. Bless you and have a good weekend and I will try to get to this on Monday!

---

### Post by aysiu on 2007-11-02
The drama never ends, for some reason.

Close the software properties and Synaptic.

Then press Alt-F2 and type ```
gksudo nautilus
``` Navigate to the /etc/apt directory and then double-click the sources.list file.

You have, as the error message indicates, duplicate sources in there. Find the entries that have the word *cdrom* in them and delete those entries. Then save and close the file.

Go back to System > Administration > Synaptic Package Manager and click *Reload*

---

### Post by marianlibrarian on 2007-11-02
Almost closing time. I did the stuff you just said in the above post. Got rid of the CDROM lines. saved and closed and then reloaded the synaptic thing.

The computer did not blow up so I am glad about that.

So does this mean I am back to the beginning again? Not a bad place since the computer is not smoking.

Thanks

---

### Post by aysiu on 2007-11-02
No, you're not back to the beginning.

If you checked off the Multiverse repositories and have Reloaded in Synaptic, then you should be able to install *acroread*, *acroread-plugins*, and *flashplugin-nonfree* through Synaptic.

Good luck!

---

### Post by bodhi.zazen on 2007-12-19
Automatix is a third party project and, at this time, is not supported on the ubuntu forums. For additional information see the following links :

	[Technical review of Ax](http://mjg59.livejournal.com/77440.html)

	To my knowledge the maintainers of Ax are working to address these issues, but they remain unresolved at this time. You might check the Ax forums for an update. When and if this occurs the situation will be re-evaluated and subject to change.

	[Official Forums Policy](http://ubuntuforums.org/announcement.php?f=13/)

	[Supported Installation Alternatives to Automatix](http://ubuntuforums.org/showthread.php?t=519872)

	[Automatix forums](http://www.getautomatix.com/forum/index.php?act=idx)

	If you want to discuss Ax, feel free to post here : 

	[http://ubuntuforums.org/forumdisplay.php?f=302](http://ubuntuforums.org/forumdisplay.php?f=302)

---

