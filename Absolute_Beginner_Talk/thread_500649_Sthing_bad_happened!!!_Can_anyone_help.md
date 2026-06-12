---
title: "Sthing bad happened!!! Can anyone help?"
date: 2007-07-14
forum: Absolute Beginner Talk
---

### Post by Grecorian on 2007-07-14
Hello I am new in Ubuntu 7.04 and i tried to install some programs. In a way I managed in some of those but in the last try...some problem was popped up in the Add/Remove Programs :

1) 'Failed to check for installed and available applications'
This is a major failure of your software management system.
Please check for broken packages with synaptic, check the file permissions and correctness of the file '/etc/apt/sources.list' and reload the software information with: 'sudo apt-get update' and 'sudo apt-get install -f'

2) Also in the update icon I can update anymore cause it sais:

'Could not initialize the package information'
A unresolvable problem occurred while initializing the package information.
Please report this bug against the 'update-manager' package and include the following error message:
'E:Type 'main' is not known on line 1 in source list /etc/apt/sources.list, E:The list of sources could not be read.'


THose are my 1st problems in Ubuntu...can anyone help me solve them?

---

### Post by deadgobby on 2007-07-14
It is telling you how to fix it. 
1. is going into Synaptic and find any broken packages.
2. Open up the terminal and 'sudo apt-get update' and 'sudo apt-get install -f'
  The other is that your sources list is mess up may be do the above.  I think once you fix the problem from doing the above. You sources list would sure it self.
Gobby

---

### Post by Grecorian on 2007-07-14
I've been in Synaptic and it has problem too! It sais:
An error Occured
E: Type 'main' is not known on line 1 in source list /etc/apt/sources.list
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.
E: _cache->open() failed, please report.

---

### Post by Grecorian on 2007-07-14
The same things it tell me and in Terminal when i give the orders :(

---

### Post by regomodo on 2007-07-14
have you edited the sources.list file?

Copy and paste to here what you get when you run

$ gedit /etc/apt/sources.list

---

### Post by Grecorian on 2007-07-14
main
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty main restricted
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty-updates main restricted
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty universe
deb [http://gr.archive.ubuntu.com/ubuntu/](http://gr.archive.ubuntu.com/ubuntu/) feisty multiverse
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) feisty-security multiverse

this what I get dude, so?

---

### Post by deadgobby on 2007-07-14
Go back to 
 gedit /etc/apt/sources.list
 where it says 
main
 I want you to put two pound signs in front of main so it would look like this
##main
 Save and then type iin the terminal 
sudo aptitude update

Gobby

---

### Post by regomodo on 2007-07-14
is that it? If so you are missing a lot. i.e deb-src http.....
So, did you edit earlier?

btw, you won't be able to save your changes with my earlier or the other guys command as you aren't super  user

$ gksudo gedit /etc/apt/sources.list

---

### Post by Grecorian on 2007-07-14
i fixed the problem guys by deleting the 'main' word as root user
i counldnt deleted it when i was simple user
I did it right? or it mustn't deleted that word?

---

### Post by Outrunner on 2007-07-14
Yes, you did it right, but there's still lines missing from your sources.list as far as I can tell... Do what deadgobby said anyway, and see what happens.

---

### Post by regomodo on 2007-07-14
yours should look a bit like this

the deb-src has been commented out as i don't think they are totally essential. Deleting the "main" is in effect the same as commenting it out, just that you can't see it anymore

[edit] i guess the link would help

[http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories)

---

