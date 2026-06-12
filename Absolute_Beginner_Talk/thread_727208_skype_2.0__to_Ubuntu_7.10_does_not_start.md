---
title: "skype 2.0  to Ubuntu 7.10 does not start"
date: 2008-03-17
forum: Absolute Beginner Talk
---

### Post by olgita on 2008-03-17
I have downloaded and installed the debian file for the latest release of Skype. And it will not start. when i launch it from the terminal, an empty window opens with title End User Licence Agreement which closes again and it says Aborted (core dumped) 
Can anyone tell me what I should do? I'm a total lambda user with no knowledge whatsoever concerning linux commands. I do use and upgrade Ubuntu since Breezy Badger. 
Thanks for your attention

---

### Post by Hospadar on 2008-03-17
I would uninstall it and install the version from medibuntu and see what happens.

Google "medibuntu" and go to the first page, the go "repoistory howto" to add the repository, then, from a command line, type "sudo apt-get install skype" to install skype out of their repositories.

Make sure you uninstall your current version first, you could use the command line "sudo apt-get remove --purge skype" or go System->Administration->Synaptic, then search, by name, for skype and remove it.

---

### Post by mikewhatever on 2008-03-17
If you insist on using Skype for Debian, perhaps you should switch to Debian first, then try again. Otherwise install the version for Ubuntu.

---

### Post by olgita on 2008-03-17
> **Hospadar said:**
> I would uninstall it and install the version from medibuntu and see what happens.

Google "medibuntu" and go to the first page, the go "repoistory howto" to add the repository, then, from a command line, type "sudo apt-get install skype" to install skype out of their repositories.

Make sure you uninstall your current version first, you could use the command line "sudo apt-get remove --purge skype" or go System->Administration->Synaptic, then search, by name, for skype and remove it.

I did what you said and now I have the old version 1.3.0.53 of Skype again :( without the video option :(, which indeed worked before. Is there anything in particular I should do to get the version 2.0.0.63 to install and  properly?
Thanks for your kind advice

---

### Post by olgita on 2008-03-17
> **mikewhatever said:**
> If you insist on useing Skype for Debian, perhaps you should switch to Debian first, then try again. Otherwise install the version for Ubuntu.

On the download page of Skype [http://www.skype.com/intl/en/download/skype/linux/choose/]("http://www.skype.com/intl/en/download/skype/linux/choose/") I chose the Ubuntu 7.04+ file which is in fact a .deb file. Hope this clears the misunderstanding. Thanks for the advice, though

---

### Post by olgita on 2008-03-17
So I did install the Skype update via the mediubuntu repository using Update manager this time and, I get the same non event. Grrrrrr.. How can I solve this? Is there anyone with an idea out there? Thanks in advance.

---

### Post by ajgreeny on 2008-03-17
Make sure you click the reload icon in synaptic before trying to install the medibuntu skype.  The only one available in my system is 2.0.0.63-0medibuntu0.7.10.1 so where you found the 1.3.0.53, I can't imagine.

---

### Post by olgita on 2008-03-17
> **ajgreeny said:**
> Make sure you click the reload icon in synaptic before trying to install the medibuntu skype.  The only one available in my system is 2.0.0.63-0medibuntu0.7.10.1 so where you found the 1.3.0.53, I can't imagine.
you are right. That's the version I have installed on my system now, as far as I can tell. But the problem of Skype not running at all still remains... Any suggestions? :confused:

---

### Post by olgita on 2008-03-17
I read in another thread that Derspankster has the same problem... I feel I'm not alone in this anymore but other than that, no Skype for me ...](*,) 
Please would anyone have a suggestion as to how to solve this? [-o<

---

### Post by LinuX-M@n1@k on 2008-03-17
try to restart your computer... maybe this will fix it (i'm not sure)

---

### Post by marko@dxlinux on 2008-03-17
i have the same problem. i would install skype on my laptop buti cant install it 'cause from the skype site clicking on download ubuntu version i have problems and i dont know how use the command line from the terminal window . to be more precise i know what i should write in the command line  "sudo apt-get install skype" but i dont know how run that.    if someone has suggestions, thanks.

---

### Post by billgoldberg on 2008-03-17
There is no need to use the command line, you can just as easily install it by going to "applications ->add/remove" or system-> administration -> synaptic package manager.

Commands are just faster and apply on most ubuntu systems (kubuntu, xubuntu, ...) , not just ubuntu.

It seems like me that you didn't remove skype before installing the medibuntu package.

Did you choose to "completely remove package" in synaptic?

Then reload, and then reinstall it.

---

### Post by olgita on 2008-03-17
Well, I tried again a restart of my system and started Skype with no other apps running and ... nada... only the "End User Licence Agreement Window" flash and that's all ...

---

### Post by olgita on 2008-03-17
> **billgoldberg said:**
> There is no need to use the command line, you can just as easily install it by going to "applications ->add/remove" or system-> administration -> synaptic package manager.

Commands are just faster and apply on most ubuntu systems (kubuntu, xubuntu, ...) , not just ubuntu.

It seems like me that you didn't remove skype before installing the medibuntu package.

Did you choose to "completely remove package" in synaptic?

Then reload, and then reinstall it.
This is what I have done twice now and with the exact same result ... :(

---

### Post by plucky on 2008-03-17
olgita,

Open a terminal and type ```
skype
``` See what error messages are produced when it doesn't start.

---

### Post by marko@dxlinux on 2008-03-17
ah ok.thanks billgoldberg.   i m trying to install skype with the synaptic but there is something wrong. i think that i have to add other repositories with "software sources" but in software sources when i click on add repositories appear a window in which is written   "enter the complete APT line of the repository that u want to add as source.       what is the APT line?     thanks for the attention

---

### Post by olgita on 2008-03-18
> **marko@dxlinux said:**
> ah ok.thanks billgoldberg.   i m trying to install skype with the synaptic but there is something wrong. i think that i have to add other repositories with "software sources" but in software sources when i click on add repositories appear a window in which is written   "enter the complete APT line of the repository that u want to add as source.       what is the APT line?     thanks for the attention
hello marko@dxlinux check  this [page]("http://t0x.in/710.html")
for instructions on how to add medibuntu to your repositories. Once you've done that and reloaded update manager, you can install Skype with synaptic package manager. And then you'll be at the same point as myself. Unless this works better for you than it does for me, which I hope for your sake.
Cheers:)

---

### Post by olgita on 2008-03-18
> **plucky said:**
> olgita,

Open a terminal and type ```
skype
``` See what error messages are produced when it doesn't start.

As I stated earlier, I get:  Aborted (core dumped) 
That's all. I have no clue what or where to look ?
Help please?

---

### Post by TeoBigusGeekus on 2008-03-18
It must be your camera:
I have a creative live cam vista which used to work flawlessly with Skype 2, after following advice from
[https://wiki.ubuntu.com/SkypeWebCams]("https://wiki.ubuntu.com/SkypeWebCams")
I even advised other people to follow that link with a feeling of self satisfaction (sorry everyone).
But after a recent update of the Ubuntu kernel, the camera simply doesn't work, no matter what I tried.
When I saw the brand new version of Skype my heart began to pound and waves of promised excitement started to drown me...:lolflag:
After I installed it, I immediatelly went to the options button to check my video. I pressed the test button and.....
Skype crashed!!!
I typed ```
skype
``` in terminal to see what messages I would get and there you go...
Exactly the same message you get!

THE END

EDIT:
I forgot to tell you that when I used the latest Skype with a Logitech Quickcam camera (absolute crap - don't buy) everything worked flawlessly...

---

### Post by olgita on 2008-03-18
I have a Logitech Quickcam which is listed in the [list]("https://wiki.ubuntu.com/SkypeWebCams") and should work 'out of the box' 
But whether I connect the webcam or not Skype aborts anyway. I'm still at loss here

---

### Post by plucky on 2008-03-18
olgita,

Just a thought,have you tried deleting the **.Skype** hidden folder in your home directory?

Skype should then try to recreate it and open the license agreement page.


Good Luck

---

### Post by Derspankster on 2008-03-18
> **plucky said:**
> olgita,

Just a thought,have you tried deleting the **.Skype** hidden folder in your home directory?

Skype should then try to recreate it and open the license agreement page.


Good Luck
Good thinking - that solved the problem! Thanks again!

---

### Post by olgita on 2008-03-18
:popcorn: I found that on an [old post]("http://ubuntuforums.org/showpost.php?p=3946169&postcount=195") with the same problem and yes! it works now. Thanks to all at this forum! you:guitar:!

---

### Post by marko@dxlinux on 2008-03-18
Hi plucky and olgita 
look at if i understand the steps in order to install skype on my 32bit linux version ( i have 5.10 version) : well
first i fave to go to the terminal and code what is necessary
than i have to install medibuntu repositories and reload from  software resources
after that i have to go to synaptic and for skype  but i cant mark for a compete removal and apply
after that i have to go to home directory and remove  what?why?
thanks for the attention

no i dont have a webcam that is working yet    that s another problem    first i want to install skype and than i will be looking for a compatible webcam

---

### Post by marko@dxlinux on 2008-03-18
plucky   i cant install
in the terminal window when i try to install is written so:  

Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) edgy/universe Sources
Hit [http://ch.archive.ubuntu.com](http://ch.archive.ubuntu.com) edgy/multiverse Sources
Downloaded 5874B in 19s (298B/s)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? (11 Resource temporarily unavailable)

i think that there is an internal problem  i dont know...

---

### Post by plucky on 2008-03-18
marko,

> i have 5.10 version I hope that is a typo and you actually mean 7.10.If it is 5.10 then none of this will work.


Open **System > Administration > Software Sources** and make sure the repositories are enabled. See  Attachment

Then you need to add the Medibuntu repository see [here](https://help.ubuntu.com/community/Medibuntu) follow the instructions to add the repository.

> after that i have to go to home directory and remove what?why?

In your home folder there are hidden files that save your configurations for installed programs.Your problem with **skype** requires you to delete this folder.Open a file browser by going to **Places > Home Folder > View > Show hidden files** delete the **skype** folder.

After that you can then reinstall skype from the Medibuntu repositories.
```
sudo apt-get update
sudo apt-get install skype
```





Good Luck

---

### Post by plucky on 2008-03-18
> E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it? (11 Resource temporarily unavailable)


You have to close Add/Remove or Synaptic package manager before using the terminal to update and install.It won't allow two package managers to run at the same time.


Good Luck

**From your last post I see that you are using Edgy Eft which is 6.10.I don't think the latest version of Skype will work with that version,but there was a version 1.4 which doesn't support webcams, in the repository.You will need to use that.**

---

### Post by marko@dxlinux on 2008-03-19
But the problem is that i dont have skype in the HIDDEN FILES of the home directory !!!

---

### Post by marko@dxlinux on 2008-03-19
i gonna explain u what i have done: 
first i go to the resource and make me sure that all first 4 boxes are marked but they are
after that i go to the terminal and code to add medibuntu repositories by coding this:
sudo wget [http://www.medibuntu.org/sources.list.d/edgy.list](http://www.medibuntu.org/sources.list.d/edgy.list) -O /etc/apt/sources.list.d/medibuntu.list
after that i go again to the terminal and code to install SKYPE       but thats what i m reading:
the followed packages have not satisfied dependencies
 j2re1.4-mozilla-plugin: Dipende: but its not going to be installed
 skype: Dipende: librte1 but its not going to be installed
E: not satisfied dipendencies. try "apt- get -f install" without packages (or try another solution)

which more things i have to do?
i tried everything
i think that i dont have the skype folder in my home folder 'because i dont have skype installed
and for sure i cant reinstall it

---

### Post by plucky on 2008-03-19
marko@dxlinux

After you installed the Medibuntu repository,did you remember to reload the indexes with ```
sudo apt-get update 
sudo apt-get upgrade
```


> E: not satisfied dipendencies. try "apt- get -f install" without packages

Try ```
sudo apt-get -f install
``` to fix the error and then ```
sudo apt-get install skype
```


Good Luck

---

### Post by sailor2001 on 2008-03-19
I think you may benefit by installing AUTOMATIX.....google that!  Skype will be listed there as well as many other apps.

---

### Post by marko@dxlinux on 2008-03-19
saior 2001

what is automatix? how can i get and install it?

---

### Post by olgita on 2008-03-20
> **sailor2001 said:**
> I think you may benefit by installing AUTOMATIX.....google that!  Skype will be listed there as well as many other apps.

Maybe you should be very careful about using Automatix  in combination with Medibuntu repository...
:rolleyes: see[ this post]("http://www.getautomatix.com/forum/index.php?showtopic=1558") on the Automatix site

---

