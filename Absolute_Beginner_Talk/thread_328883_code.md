---
title: "code"
date: 2006-12-31
forum: Absolute Beginner Talk
---

### Post by CriticalStealth on 2006-12-31
everyone is talking about code to apply settings, and install things.. ok, so how do i input code to install things and such.

---

### Post by taurus on 2006-12-31
Install automatix2 and use it to install codecs and other media stuff...

[http://www.getautomatix.com/](http://www.getautomatix.com/)

---

### Post by CriticalStealth on 2006-12-31
ok, thank you


hope id ont sound dumb, but i cannot find where ot download it.. directions please :)

---

### Post by taurus on 2006-12-31
Do you see the **Installation** link to the left???

---

### Post by CriticalStealth on 2006-12-31
haha OH, missed that one, thanks man!

---

### Post by CriticalStealth on 2006-12-31
it gets fatal errors when installing numorous things, the only thing out of all the things i told it to install that finished was azureus..... msn and such, could not finish, thye got fatal errors. any thoughts on that?

---

### Post by taurus on 2006-12-31
Paste the output of this command here?

Applications -> Accessories -> Terminal
```
cat /etc/apt/sources.list
```
Now, tell me exactly what you did so I would know what's wrong with it...

---

### Post by CriticalStealth on 2006-12-31
i installed automatix... opened it up, clicked some boxes on programs i wnated to install, then hit Start.. thats it thats all!

---

### Post by taurus on 2006-12-31
You add a line to your /etc/apt/sources.list, import a key (or gpq), update the list, install automatix2, fireup automatix2 (from Applications -> System Tools -> Automatix), and install other stuff from the list!!!

That's how you would do it...

---

### Post by CriticalStealth on 2006-12-31
wow, i dont even o what your telling me to do,.. thats confusing for sure...


i am now gettign a pop up telling em that my system needs to be updated, but there is a brokenit tells me to use the broekn package filter to locate it...... im confused:confused: :confused:

add a what to my what you say?

---

### Post by taurus on 2006-12-31
What's why I asked you exactly what you did to install automatix2?  If I know what you did, perhaps I could figure out how to fix it...

---

### Post by riven0 on 2006-12-31
Also, make sure you followed the directions for your version of Ubuntu. Are you using Dapper or Edgy?

---

### Post by CriticalStealth on 2006-12-31
its 6.10 i386    i tink edgy.. im not positive

---

### Post by riven0 on 2006-12-31
> **CriticalStealth said:**
> its 6.10 i386    i tink edgy.. im not positive

So then, did you follow these instructions? Open the terminal: Applications >> Accessories >> Terminal. Copy and paste these 1 at a time:
> 
echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list

> wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
> 
gpg --import key.gpg.asc

> gpg --export --armor 521A9C7C | sudo apt-key add -
> 
sudo apt-get update && sudo apt-get install automatix2

---

### Post by CriticalStealth on 2006-12-31
when i go to paste them in, nothing shows up in the terminal.   and i dont really understand that terminal thing yet, what does it do, and how do i use it?

---

### Post by macogw on 2006-12-31
The terminal is like DOS on Windows, but a lot more powerful.  It can do anything you can do by clicking with your mouse and more.  That's how you give commands to your computer.  Don't use ctrl+v and ctrl+c for the copy/paste because ctrl+c is a command in the terminal that says "wait! stop that!" and ends the current process.  Use the right-click way of copying and pasting.  

We give directions using the terminal because we don't always know where you've moved certain buttons, and the "click there....no...no, there....up....no....down a bit....yeah, there" effect is annoying.  The terminal is called bash, and it is the same on Linux and Mac OS X computers, so it's an easy way for us to give help (because it's universal-ish).

---

### Post by CriticalStealth on 2006-12-31
ok, ill try again, thanks

---

### Post by riven0 on 2006-12-31
> **CriticalStealth said:**
> when i go to paste them in, nothing shows up in the terminal.   and i dont really understand that terminal thing yet, what does it do, and how do i use it?

The easiest way to explain the terminal is that it is similar to MS-DOS, except much more powerful. In fact, in Linux, its not required to use a graphical environment, everything can be run from the terminal.

Nothing showed up in the terminal even after you did **sudo apt-get update && sudo apt-get install automatix2**? Strange. You were hitting enter after each command, right? 

Well, try re-opening the terminal, copy and pasting this and hit enter:

> automatix2  

If that doesn't bring up anything, try this instead:

> automatix

---

### Post by CriticalStealth on 2006-12-31
i dont think i did this right.. heres my terminal.. tell me what i did wrong...

lopes@lopeslinux:~$ sudo tee -a /etc/apt/sources.list mQGiBESDLOwRBAC0UwJJgmJ0GWL0DZvTrZq/754uEg1Adx/37Sa6pRYku3JzH69C
Password:
Sorry, try again.
Password:
tee: mQGiBESDLOwRBAC0UwJJgmJ0GWL0DZvTrZq/754uEg1Adx/37Sa6pRYku3JzH69C: No such file or directory
import key.gpg.asc sudo apt-key add - sudo apt-get update && sudo apt-get install automatix2

---

### Post by macogw on 2006-12-31
What's the gibberish?  It should end at /etc/apt/sources.list  You missed the first half of that line, though.  Get rid of all the gibberish.  I think it tried to copy some of the quotey internet box...

---

### Post by CriticalStealth on 2006-12-31
i oput in this

sudo apt-get update && sudo apt-get install automatix2 

and hit enter, and some crazy code went scrolling down, i made me excited lol... not what? close it?

---

### Post by riven0 on 2006-12-31
> **CriticalStealth said:**
> i oput in this

sudo apt-get update && sudo apt-get install automatix2 

and hit enter, and some crazy code went scrolling down, i made me excited lol... not what? close it?

No, no. Now copy and paste this and hit enter:
> 
automatix2

If that brings up nothing, then try:
> 
automatix

---

### Post by macogw on 2006-12-31
Did you go through the rest of the stuff without errors before that happened?  automatix still won't work if you didn't clear up the gibberish issues and the errors you got before.

---

### Post by CriticalStealth on 2006-12-31
ya i think it should work, im gonna try it now



EDIT= uh oh.. it didnt work.. what do i do!! i just wanna dl the msn lol!!!!

---

### Post by CriticalStealth on 2006-12-31
ok so i went back and re entered all the code he gave me in thoise quote sin order

copy>pasted them> hit enter> again


this is the code in my terminal at the moment, i have not closed it yet

lopes@lopeslinux:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
lopes@lopeslinux:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--12:05:06--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s             

12:05:06 (86.83 MB/s) - `key.gpg.asc' saved [1730/1730]

lopes@lopeslinux:~$ gpg --import key.gpg.asc
gpg: /home/lopes/.gnupg/trustdb.gpg: trustdb created
gpg: key 521A9C7C: public key "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lopes@lopeslinux:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
lopes@lopeslinux:~$  sudo apt-get update && sudo apt-get install automatix2
E: Type 'gpg' is not known on line 51 in source list /etc/apt/sources.list
lopes@lopeslinux:~$ Reply With Quote
bash: Reply: command not found
lopes@lopeslinux:~$

---

### Post by riven0 on 2006-12-31
> **CriticalStealth said:**
> ok so i went back and re entered all the code he gave me in thoise quote sin order

copy>pasted them> hit enter> again


this is the code in my terminal at the moment, i have not closed it yet

lopes@lopeslinux:~$ echo "deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main" | sudo tee -a /etc/apt/sources.list 
deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main
lopes@lopeslinux:~$ wget [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
--12:05:06--  [http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
           => `key.gpg.asc'
Resolving [www.getautomatix.com](www.getautomatix.com)... 82.165.193.29
Connecting to www.getautomatix.com|82.165.193.29|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 1,730 (1.7K) [text/plain]

100%[====================================>] 1,730         --.--K/s             

12:05:06 (86.83 MB/s) - `key.gpg.asc' saved [1730/1730]

lopes@lopeslinux:~$ gpg --import key.gpg.asc
gpg: /home/lopes/.gnupg/trustdb.gpg: trustdb created
gpg: key 521A9C7C: public key "Justin Hayes (Automatix Repository Master) <wildtangent@w1ldt4ng3nt.net>" imported
gpg: Total number processed: 1
gpg:               imported: 1
lopes@lopeslinux:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
OK
lopes@lopeslinux:~$  sudo apt-get update && sudo apt-get install automatix2
E: Type 'gpg' is not known on line 51 in source list /etc/apt/sources.list
lopes@lopeslinux:~$ Reply With Quote
bash: Reply: command not found
lopes@lopeslinux:~$

Hmm, is there something wrong with your sources.list? Can you do this so I can look at it?:

> sudo gedit /etc/apt/sources.list

That should bring up the text editor with your sources. Now copy and paste all the contents here.

---

### Post by CriticalStealth on 2006-12-31
this si everything in there.. EVERYTHING


deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) edgy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security main restricted
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) edgy-security universe


#AUTOMATIX REPOS START

deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) dapper-commercial main

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-backports main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-updates universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy-security main restricted universe multiverse

deb [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) edgy universe multiverse
#AUTOMATIX REPOS END
gpg --export --armor 521A9C7C | sudo apt-key add - 




deb [http://www.getautomatix.com/apt](http://www.getautomatix.com/apt) edgy main

---

### Post by macogw on 2006-12-31
> **CriticalStealth said:**
> ya i think it should work, im gonna try it now



EDIT= uh oh.. it didnt work.. what do i do!! i just wanna dl the msn lol!!!!

You can login to msn messenger using Gaim (Applications > Internet > Gaim Internet Messenger)

```
sudo gedit /etc/apt/sources.list
```
delete this line:
gpg --export --armor 521A9C7C | sudo apt-key add -
save it

---

### Post by CriticalStealth on 2006-12-31
ya i use the gaim, but i wabt the real one, with video support.. i will delete the line....

---

### Post by macogw on 2006-12-31
easiest way:
[http://amsn-project.net/linux-downloads.php](http://amsn-project.net/linux-downloads.php)
Download that to your desktop.  Right click on it and tell it to be executable.  Then double click.  A terminal will come up.  Let it do it's thing.  It's setting up auto-package.  Double click on the .package file again.  It'll run an installer similar to what you see in Windows but without clicking "next" 30 times.

---

### Post by CriticalStealth on 2006-12-31
it coudlny do it... i double clicked the package, and it had some error, saying ti could not do this, some thing do with gedit something was not found.


i did something wrong, my automatix wont open now, i loads, then doesnt open.. uh oh!

---

### Post by macogw on 2006-12-31
gpg --export --armor 521A9C7C | sudo apt-key add -

put that in the terminal and hit enter. for some reason it went into your sources.list before and shouldn't have.  then do "sudo apt-get update" again.


For the aMSN installer, did you right click and go to properties then tell it to be executable before you double clicked on it?  Try using right-click "open" instead of double-clicking.  Tell it to run.  A terminal should come up and do some stuff.  Then right-click "open" "run" again.

---

### Post by CriticalStealth on 2006-12-31
lopes@lopeslinux:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
Password:
OK
lopes@lopeslinux:~$ sudo apt-get update
E: Type 'link' is not known on line 57 in source list /etc/apt/sources.list
lopes@lopeslinux:~$ 


this is the code i got when i did what you said to.

---

### Post by riven0 on 2006-12-31
> **CriticalStealth said:**
> lopes@lopeslinux:~$ gpg --export --armor 521A9C7C | sudo apt-key add -
Password:
OK
lopes@lopeslinux:~$ sudo apt-get update
E: Type 'link' is not known on line 57 in source list /etc/apt/sources.list
lopes@lopeslinux:~$ 


this is the code i got when i did what you said to.

:confused: So weird. Okay, forget about doing sudo apt-get update for a minute and just do:

> sudo apt-get install automatix2

---

### Post by macogw on 2006-12-31
[http://www.getautomatix.com/apt/key.gpg.asc](http://www.getautomatix.com/apt/key.gpg.asc)
File > Save Page As... and save that to your desktop

System > Administration > Synaptic Package Manager
put in your password
Settings > Repositories
Click "Authentication" then "Import Key"
Click on the file you just saved to your desktop

---

### Post by CriticalStealth on 2007-01-01
ok i did exactly what you just told me to, and i think everything worked out fine.. what was it it was supposed to do though?

---

### Post by CriticalStealth on 2007-01-01
i got this error today

[COLOR="Black"][SIZE="5"]Failed to check for installed and available applications[/SIZE][/COLOR]
This is a major failure of your software management system. Check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information: 'sudo apt-get update'.

---

