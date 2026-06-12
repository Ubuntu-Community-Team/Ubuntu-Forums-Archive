---
title: "Installing Skype on 7.10 Gutsy"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by L Campbell on 2007-10-20
I just upgraded, today, to Gutsy and I see that the latest version of Skype is for Feisty.

Should that work with Gutsy?

Anyone tried it?

Thanks.

---

### Post by alvinistic on 2007-10-20
Yes, it works with Gutsy. I'm using it :)

---

### Post by bluenova on 2007-10-20
Working fine here.

---

### Post by techpr on 2007-10-20
Yes, it works fine on 7.10

---

### Post by andreiterente on 2007-10-20
hello, i have a problem with the install
"skype:
 Depends: libqt4-core (>=4.2.1) but it is not installable
 Depends: libqt4-gui (>=4.2.1) but it is not installable"
i tried to put this address in the repositories [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) and i still get that error.
i looked all over this forum but nothing works
i'm trying to install skype 1.4.0.118 on gutsy
please help

---

### Post by L Campbell on 2007-10-22
> **andreiterente said:**
> hello, i have a problem with the install
"skype:
 Depends: libqt4-core (>=4.2.1) but it is not installable
 Depends: libqt4-gui (>=4.2.1) but it is not installable"
i tried to put this address in the repositories [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) and i still get that error.
i looked all over this forum but nothing works
i'm trying to install skype 1.4.0.118 on gutsy
please help

Did you go to the Skype website ans download from there?

---

### Post by Fanin on 2007-10-23
i have the same problem.. i download skype, get the package, but i cant install it
"Error: Dependency is not satisfiable: libqt4-core" :confused:

---

### Post by evilregis on 2007-10-23
Go to System -> Administration -> Synaptic Package Manager and Search for libqt4-core.  Mark it for installation, Apply.  I think I had to do this to get Skype to install for me as well if memory serves me well.

---

### Post by Fanin on 2007-10-23
> **evilregis said:**
> Go to System -> Administration -> Synaptic Package Manager and Search for libqt4-core.  Mark it for installation, Apply.  I think I had to do this to get Skype to install for me as well if memory serves me well.

i did that, but i couldn't find libqt4-core in synaptic package manager

---

### Post by andreiterente on 2007-10-23
i had this problem and i resolved it... go to System - administration - Synaptic - Settings - repositories - (check all from "downloadable from the internet") - put this "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" in third party software with add.
now reload the packages - search for skype in synaptic packedge manager (it should be their) and install it.
it should work !!! tell me if you made it.

---

### Post by Fanin on 2007-10-23
> **andreiterente said:**
> i had this problem and i resolved it... go to System - administration - Synaptic - Settings - repositories - (check all from "downloadable from the internet") - put this "deb [http://download.skype.com/linux/repos/debian/](http://download.skype.com/linux/repos/debian/) stable non-free" in third party software with add.
now reload the packages - search for skype in synaptic packedge manager (it should be their) and install it.
it should work !!! tell me if you made it.

it almost worked.. but when i mark skype for installation it says:
"could not mark all packages for installation or upgrade"
"skype:
 Depends: libqt4-core (>=4.2.1) but it is not installable
 Depends: libqt4-gui (>=4.2.1) but it is not installable"

:confused:

---

### Post by andreiterente on 2007-10-23
try checking in repositories -  third party - the 2 party's  (partner and partner source...) and in updates the first two (important security.. and recommended... )and try it again

---

### Post by andreiterente on 2007-10-23
and do not forget to refresh the repositories !!!

---

### Post by Fanin on 2007-10-23
> **andreiterente said:**
> try checking in repositories -  third party - the 2 party's  (partner and partner source...) and in updates the first two (important security.. and recommended... )and try it again

the same error:
"skype:
 Depends: libqt4-core (>=4.2.1) but it is not installable
 Depends: libqt4-gui (>=4.2.1) but it is not installable"
:mad:

---

### Post by andreiterente on 2007-10-23
please believe me that i don't know what is the problem because that is what i did to make it work .
You could check again that you have all repositories checked (you should have 52 updates or how are they called) and try again .
I'm sorry but i can't be of more help.
Verify if you are installing skype 1.4
good luck

---

### Post by Fanin on 2007-10-23
> **andreiterente said:**
> please believe me that i don't know what is the problem because that is what i did to make it work .
You could check again that you have all repositories checked (you should have 52 updates or how are they called) and try again .
I'm sorry but i can't be of more help.
Verify if you are installing skype 1.4
good luck

thank you very much for your help and time
i really do appreciate it! :)

---

### Post by rudeboyskunk on 2007-10-23
This is a repository problem (I had the same problem when I first installed Gutsy because I forgot to enable all repositories).  Just do what everyone else has said so far, and enable the unchecked repositories in System>Administration>Software Sources.

---

### Post by leexgx on 2007-10-23
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095) if any one who is can change that status can you please set that bug as med or high, as its an bug that should not be apart of the Live CD

goto System > Admin > software sources

1 Tick all boxs apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options
4 [Optional] change the auto up date check to [Download all updates in background] (assuming you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)

I do not recommend auto install with out confirmation Option as it may not wait for all updates to be install when shuting down the pc, as it make brake your box

---

### Post by Fanin on 2007-10-23
> **leexgx said:**
> [https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/154095) if any one who is can change that status can you please set that bug as med or high, as its an bug that should not be apart of the Live CD

goto System > Admin > software sources

1 Tick all boxs apart form source code (do not think norm users need that)
2 Pick your Download From server location (as it picks main server by default click on search if you cant see one for you)
3 Goto updates and tick the first 2 options
4 [Optional] change the auto up date check to [Download all updates in background] (assuming you do not have an hard disk that is very small its an better option so your ready to install when you are ready just means you do not need to have to wait for them to download)

I do not recommend auto install with out confirmation Option as it may not wait for all updates to be install when shuting down the pc, as it make brake your box

WOOHOO
it worked.. i did what you said and it works perfectly :)
thank you very very much :biggrin:

---

### Post by prosper927 on 2007-10-23
I would like to ask how i would be able to install Skype for 7.10 Gutsy on 64bit AMD PC. Help.:(

---

### Post by sporto on 2007-10-24
> **prosper927 said:**
> I would like to ask how i would be able to install Skype for 7.10 Gutsy on 64bit AMD PC. Help.:(

I followed Cappy's guide which worked perfectly:
[http://ubuntuforums.org/showthread.php?t=432295&highlight=skype](http://ubuntuforums.org/showthread.php?t=432295&highlight=skype)

:KS

---

