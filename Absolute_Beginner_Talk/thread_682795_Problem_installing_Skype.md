---
title: "Problem installing Skype"
date: 2008-01-30
forum: Absolute Beginner Talk
---

### Post by flyboy340 on 2008-01-30
When I try to install I get the following error;

Error: Dependancy is not satisfiable: libqt4-core

I am a complete newbie with Linux :(

---

### Post by Aurora@FleetBuzz on 2008-01-30
Are you installing via the Synaptic Package Manager?  I did and have had no problems, other than having to configure my headset & mic in alsamixer.

---

### Post by jclmusic on 2008-01-30
three options to solve this problem...

1. download from [http://www.skype.com](http://www.skype.com), and double click the .deb file. it will automatically install the dependencies this way. (i think this is a newer version than the repos too, so might be the best idea).

2. open synaptic (system > administration > synaptic package manager), search for skype, tag and install. this should also automatically tag all dependencies.

3. open a terminal, run "sudo apt-get install libqt4-core", and then run the skype installation again.

---

### Post by flyboy340 on 2008-01-30
Well I tried all three suggestions.

When I try the first one, the "package installer" gives the same error I stated above, and the "install package" icon is grayed out.

When I try the second suggestion, there is no Skype package available for selection.

When I try the thirs suggestion, I get an error "Couldn't find package libqt4-core

**I should also mention I'm running XUbuntu...**

---

### Post by jan quark on 2008-01-30
perhaps your sources are not enabled?

go to the sources window in the menu ( dont recall the exact location, using mint,somewhere in the administration perhaps)

and check all available sources 
then 
sudo apt-get update into the terminal
and try to install again the needed package

---

### Post by CJ56 on 2008-01-30
If you go to Medibuntu -

[www.medibuntu.org/index.php](www.medibuntu.org/index.php)

Follow the instructions in the Repository HowTo

Make sure that the Medibuntu repository is enabled in Synaptic - 

Then search for Skype in Synaptic & it should be there. Just follow the usual Synaptic instructions after that

Medibuntu actually has a number of useful free and non-free applications. Worth a look around... :)

---

### Post by flyboy340 on 2008-01-30
Thanks for all the help guys :)

What a steep learning curve! I was able to install by installing the libqt4-gui application and Skype installed after that :)

---

### Post by jan quark on 2008-01-30
good to hear
one step at a time :)

please mark this thread as solved 
use the thread tools at the top 
thank you

---

### Post by Aurora@FleetBuzz on 2008-01-30
Here's a good resource for adding repositories:
[http://www.psychocats.net/ubuntu/sources#gutsy](http://www.psychocats.net/ubuntu/sources#gutsy)
Follow the instructions for the dialog boxes that will appear after you select

> System > Administration > Software Sources

---

### Post by sunseeker888 on 2008-02-02
> **jclmusic said:**
> three options to solve this problem...

1. download from [http://www.skype.com](http://www.skype.com), and double click the .deb file. it will automatically install the dependencies this way. (i think this is a newer version than the repos too, so might be the best idea).

2. open synaptic (system > administration > synaptic package manager), search for skype, tag and install. this should also automatically tag all dependencies.

3. open a terminal, run "sudo apt-get install libqt4-core", and then run the skype installation again.




HI I have done the install? this version , I can not send sms message & skypeout and view my account history etc, is that correct?


Cheers

irwin:confused:

---

