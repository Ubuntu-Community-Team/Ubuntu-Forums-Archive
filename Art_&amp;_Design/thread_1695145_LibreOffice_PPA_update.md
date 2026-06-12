---
title: "LibreOffice PPA update?"
date: 2011-02-25
forum: Art &amp; Design
---

### Post by teejay17 on 2011-02-25
Can anyone tell me when/if LibreOffice will update the PPA to 3.3.1? It's been out for a few days already, and still the updated PPA hasn't come down the line...

---

### Post by teejay17 on 2011-02-25
I should have also specified that I'm using Lucid and so this question pertains to LibreOffice PPA for Lucid.

---

### Post by OooBuntuRox on 2011-02-26
> **teejay17 said:**
> I should have also specified that I'm using Lucid and so this question pertains to LibreOffice PPA for Lucid.

As part of the libreOffice install, I ran these lines in a terminal window:

 [COLOR=#0000ff][SIZE=4][I]sudo add-apt-repository ppa:libreoffice/ppa
sudo apt-get update
sudo apt-get install libreoffice[/I][/SIZE][/COLOR]
 
I tried to update and I am getting an error message. 

Here is the error message that I am getting in a pop-up window:
[COLOR=Blue]
Requires installation of untrusted packages

The action would require the installation of packages from not authenticated sources.[/COLOR]

If no one comes up with a solution/ fix in the next couple of months,  the problems will probably go away in release 11.04 I believe that  LibreOffice will be included with the new distribution rather than  OpenOffice.

Still, if anyone has a better answer, I'd like to hear it too.

Good luck/ Thanks, OoobuntuRox :guitar:

---

### Post by ubuntu27 on 2011-02-26
> **OooBuntuRox said:**
> 
Requires installation of untrusted packages

1) Go to [this website]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444"): 

2) Copy everything from "----BEGIN PGP PUBLIC KEY BLOCK-----" to "-----END PGP PUBLIC KEY BLOCK-----"

and pate it on a text editor such as Gedit.
Save it as libreoffice**.key**

3)Open Synaptic Package Manager (Ubuntu) or KPackageKit (kubuntu)


4a) in Synaptic: Tools---> Software Sources

4b)in kPackagekit: Settings--->Edit Origins

5) Go to "Authentication"

6) Click on "Import Keys"

7) Select the name.key file that you saved in step 2.

8) Press ok or Confirm.

9) Close the window.

10) Update the repository. (RELOAD)

---

### Post by OooBuntuRox on 2011-02-26
> **ubuntu27 said:**
> 1) Go to [this website]("http://keyserver.ubuntu.com:11371/pks/lookup?op=get&search=0x83FBA1751378B444"): 



Hello ubuntu27,

Thanks for the solution. It looks like it will work. The only problem right now is the website connection is timing out.

I'll have to try it again later.

OooBuntuRox :guitar:

---

### Post by CarpKing on 2011-02-26
Doesn't "apt-add ppa" usually get the key for you?  Maybe the site was timing out then too.

---

### Post by OooBuntuRox on 2011-02-26
> **CarpKing said:**
> Doesn't "apt-add ppa" usually get the key for you?  Maybe the site was timing out then too.

Well I have to admit, I followed and trusted the solution I found in a web search about a month ago. I didn't notice the problem until 2 days ago when I attempted the update.

So CarpKing, it seems you may be correct as well. I tried running this command once more: 

[COLOR=#0000ff][SIZE=4]*sudo add-apt-repository ppa:libreoffice/ppa*[/SIZE][/COLOR]

I thought perhaps it might be related to user privilleges during the recent previous attempt. But that isn't it. Below are the beginning and end lines of the keyserver response:

Executing: gpg .....
.......
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

So again, yes, it is still timing out for me.

OooBuntuRox, :guitar:

---

### Post by ubuntu27 on 2011-02-26
> **CarpKing said:**
> Doesn't "apt-add ppa" usually get the key for you?  Maybe the site was timing out then too.

I guess I am old fashioned.
That apt-add ppa was new on maverick wasn't it? I never used it.

---

### Post by DougieFresh4U on 2011-02-26
I just did updates and there were several LibreOffice updates, don't remember what they were

---

### Post by brookie on 2011-02-26
looks like someone updated the maverick version but not the lucid version yet
you can check it out on the launchpad site

[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Elibreoffice/+archive/ppa?field.series_filter=")

---

### Post by OooBuntuRox on 2011-02-27
> **brookie said:**
> looks like someone updated the maverick version but not the lucid version yet
you can check it out on the launchpad site

[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Elibreoffice/+archive/ppa?field.series_filter=")

I'm running Maverick [10.10] and I'm getting the error messages. I tried playing around with the lucid, maverick, and natty repositories. I double checked The versions numbers of Ubuntu and LibreOffice. I think my installation of LibreOffice may already be up to date. Perhaps not:

LibreOffice 3.3.0 
OOO330m19 (Build:6)
tag libreoffice-3.3.0.4, Ubuntu package 1:3.3.0-1maverick1

I'd like to know more, but I'm not too worried since 11.04 will be here soon enough.

OooBuntuRox, :guitar:

[SIZE=3][SIZE=2]By the way, using the GUI  for repository updates seems a little easier than the command line:[/SIZE]
[/SIZE] 
[http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them](http://askubuntu.com/questions/4983/what-are-ppas-and-how-do-i-use-them)

---

### Post by teejay17 on 2011-02-27
> **brookie said:**
> looks like someone updated the maverick version but not the lucid version yet
you can check it out on the launchpad site

[https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=]("https://launchpad.net/%7Elibreoffice/+archive/ppa?field.series_filter=")

Yes, the Maverick versions updated automatically, and work well. They came down the line on Friday evening. Now we just have to wait for Lucid; unfortunately, the latest message on the Launchpad [site]("https://launchpad.net/~libreoffice/+archive/ppa?field.series_filter=") for Lucid says "failed to build." Looks like something went wrong. Hopefully it gets fixed soon.

---

### Post by teejay17 on 2011-02-27
Hey everyone, the PPA for LibreOffice has been updated for Lucid. It's installing on my system as I type this.

---

### Post by OooBuntuRox on 2011-03-01
> **teejay17 said:**
> Yes, the Maverick versions updated automatically, and work well. They came down the line on Friday evening. Now we just have to wait for Lucid; unfortunately, the latest message on the Launchpad [site]("https://launchpad.net/%7Elibreoffice/+archive/ppa?field.series_filter=") for Lucid says "failed to build." Looks like something went wrong. Hopefully it gets fixed soon.


I don't know what's going on on my end. I'm still getting an error. If it were up tp date, it would simply say so. I shouldn't be getting errors. Any ideas anyone?

**Requires installation of untrusted packages**

The action would require the installation of packages from not authenticated sources.

details:

libreoffice libreoffice-base libreoffice-base-core libreoffice-calc libreoffice-common libreoffice-core libreoffice-draw libreoffice-emailmerge libreoffice-filter-mobiledev libreoffice-impress libreoffice-java-common libreoffice-math libreoffice-report-builder-bin libreoffice-style-galaxy libreoffice-writer python-uno ttf-opensymbol uno-libs3 ure

Changes for the versions:
1:3.3.0-1maverick1
1:3.3.1-1ubuntu3~maverick1

This change is not coming from a source that supports changelogs.This change is not coming from a source that supports changelogs.

Thanks,
OooBuntuRox :guitar:

---

### Post by OooBuntuRox on 2011-03-02
> **OooBuntuRox said:**
> Hello ubuntu27,

Thanks for the solution. It looks like it will work. The only problem right now is the website connection is timing out.

I'll have to try it again later.

OooBuntuRox :guitar:
[SIZE=3][B]

[COLOR=Blue]UPDATE:[/COLOR][/B][/SIZE]
[SIZE=2]
I still can't get the keyring. Can it be entered manually? I need the LibreOffice Keyring for Maverick. Can someone post it here?

Applications> Ubuntu Software center> Edit> Software Sources> 

Then click on the Authentication Tab and look in the "Trusted Software Providers" window.

Thanks, [/SIZE]OooBuntuRox :guitar:

---

### Post by teejay17 on 2011-03-02
> **OooBuntuRox said:**
> [SIZE=3][B]

[COLOR=Blue]UPDATE:[/COLOR][/B][/SIZE]
[SIZE=2]
I still can't get the keyring. Can it be entered manually? I need the LibreOffice Keyring for Maverick. Can someone post it here?

Applications> Ubuntu Software center> Edit> Software Sources> 

Then click on the Authentication Tab and look in the "Trusted Software Providers" window.

Thanks, [/SIZE]OooBuntuRox :guitar:
I'm not really sure if I understand your question. Usually, keyrings are a personal thing, something you establish when you install Ubuntu for the first time. They can be edited under Applications>Keyring Manager.

---

### Post by bapoumba on 2011-03-02
Please try :
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444 

```

The key is on LibreOffice ppa : [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa)

---

### Post by OooBuntuRox on 2011-03-05
> **bapoumba said:**
> Please try :
```
sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444 

```The key is on LibreOffice ppa : [https://launchpad.net/~libreoffice/+archive/ppa]("https://launchpad.net/%7Elibreoffice/+archive/ppa")

[SIZE=3]After entering the line: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444 
in a terminal window, here are the results.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1378B444
gpg: requesting key 1378B444 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Thanks, OooBuntuRox [/SIZE]:guitar:

---

### Post by bapoumba on 2011-03-05
> **OooBuntuRox said:**
> [SIZE=3]After entering the line: sudo apt-key adv --keyserver keyserver.ubuntu.com --recv-keys 1378B444 
in a terminal window, here are the results.

Executing: gpg --ignore-time-conflict --no-options --no-default-keyring --secret-keyring /etc/apt/secring.gpg --trustdb-name /etc/apt/trustdb.gpg --keyring /etc/apt/trusted.gpg --primary-keyring /etc/apt/trusted.gpg --keyserver keyserver.ubuntu.com --recv-keys 1378B444
gpg: requesting key 1378B444 from hkp server keyserver.ubuntu.com
gpg: keyserver timed out
gpg: keyserver receive failed: keyserver error

Thanks, OooBuntuRox [/SIZE]:guitar:

Very strange, I tested the code line myself before giving it to you and it worked. I'll have to think this over..

---

### Post by OooBuntuRox on 2011-03-06
> **bapoumba said:**
> Very strange, I tested the code line myself before giving it to you and it worked. I'll have to think this over..

[SIZE=3]It seems you understand much more about it than I do. Please excuse me, but, could it possibly be related to any software center settings?
[/SIZE]
[SIZE=2]Thanks, OooBuntuRox [/SIZE]:guitar:

---

### Post by bapoumba on 2011-03-06
Would you happen to be behind a firewall ?

---

### Post by OooBuntuRox on 2011-03-06
> **bapoumba said:**
> Would you happen to be behind a firewall ?

Yes. Both physical and software. I tried turning off the software firewall but it didn't seem to make any difference. That is also why I wondered if I could add the key information manually through software center.

There must be a fix aside from turning the firewall off. That would be horrible security. I'll bet when 11.04 is released it will work without a hitch.

Thanks for hanging in there this long.Any other thoughts?

OooBuntuRox, :guitar:

---

### Post by teejay17 on 2011-03-27
3.3.2. has been out for a week now, but no PPA update yet.

---

### Post by erikdstock on 2011-03-27
would this be the reason i can't install libreoffice or reinstall my (just removed) openoffice? added the ppa and was going through the steps last night and now i get an error for either case about how this requires packages that "won't be installed" or something to that effect. this happens with apt-get, software center and synaptic and i can't even go back to ooo and i'm freaking out because i NEED a productivity suite tonight! (central US time, which is now).

will this fix itself or what? i've read other places that this is about the ppa not being updated and that i should try back later, but this problem began yesterday afternoon.

---

### Post by 23dornot23d on 2011-03-28
Did you try the [open office site and download a deb]("http://download.openoffice.org/other.html") file ....... clicking these should install form the Software Centre or from the Gdebi package installer .... (the reason I give the open office link - is that you obviously had this successfully running before) but Libre Office seems the latest now to be used by Ubuntu.


The other thing is - PPA's can be good for latest releases .... but if there is any dependency problems in them then sometimes it is best to remove the added and offending PPA ..... if dependencies become an issue .....


Hope you get/got it running .....

---

### Post by daniele80 on 2011-06-18
still waiting for LibreOffice 3.4 on the ppa...

---

### Post by jeremy on 2011-07-17
> **daniele80 said:**
> still waiting for LibreOffice 3.4 on the ppa...

And me too, stiiiiil waiting..... :(

---

### Post by teejay17 on 2011-07-20
> **jeremy said:**
> And me too, stiiiiil waiting..... :(

Yeah me too. I bet they are probably waiting for the 26th, when they release 3.4.2 (the one that's good for Corporate) to worry about PPAs. That's just my guess.

---

### Post by sancho panza on 2011-08-02
I'm getting the feeling that the latest Libreoffice is not gonna show up in the existing Libreoffice PPA. I do not fully understand the reasons why.
I wish someone with the knowledge sets up another Libreoffice PPA with the latest versions for adventurous users of Libreoffice. Sigh!

---

### Post by teejay17 on 2011-08-02
> **sancho panza said:**
> I'm getting the feeling that the latest Libreoffice is not gonna show up in the existing Libreoffice PPA. I do not fully understand the reasons why.
I wish someone with the knowledge sets up another Libreoffice PPA with the latest versions for adventurous users of Libreoffice. Sigh!
I actually followed the directions _[here]("http://www.libre-software.net/how-to-install-libreoffice-on-ubuntu-linux-mint")_ and it went well, without a hitch. 
The only thing you should be aware of, should you choose this method, is that when you extract the file in your downloads folder, you will have to rename part of it to "3.4.2" and not "3.4.2rc3," so that the command will work (another way to say it is *make sure the name of the file you are trying to install matches the command). *

---

### Post by sancho panza on 2011-08-02
I know it can be installed from the libreoffice website, but I wanted a PPA so that things go smoothly and automatically. More importantly, future updates would also be equally automatic. Another minor concern with the website download is potential dependency complications.

---

### Post by cpatrick08 on 2011-08-02
> **sancho panza said:**
> I know it can be installed from the libreoffice website, but I wanted a PPA so that things go smoothly and automatically. More importantly, future updates would also be equally automatic. Another minor concern with the website download is pote**pa:libreoffice/ppa**           ntial dependency complications.
there is one at [https://launchpad.net/~libreoffice/+archive/ppa](https://launchpad.net/~libreoffice/+archive/ppa) which is  p**pa:libreoffice/ppa**

---

### Post by teejay17 on 2011-08-02
> **sancho panza said:**
> I know it can be installed from the libreoffice website, but I wanted a PPA so that things go smoothly and automatically. More importantly, future updates would also be equally automatic. Another minor concern with the website download is potential dependency complications.

I understand. I usually like PPAs as well, but it's taking forever...
As far as dependencies, all was okay this time around for 3.4.2. And man, is it ever fast compared to the older version in Ubuntu. 
The next major release, I will attempt to purge my system of 3.4.2 and re-install the next .deb file. Hopefully that will work. Perhaps with LibreOffice, at least, PPAs won't be necessary.

---

