---
title: "About MLDonkey"
date: 2006-12-16
forum: Absolute Beginner Talk
---

### Post by chrishoeppner on 2006-12-16
Hi there!

I'm pretty new to the whole linux thing, but I decided to make step away from windows. Someone talked me about mldonkey and it's features. I was mainly impressed by the fact that it's able to run as a system service and therefor being able to startup on it's own with the system, independently of user sessions or else. So I made a google search and got very poor results. There seems to be a big lack of information about mldonkey.

So far I have been able to compile my own mldonkey-server into a custom folder in my home directory. However, and after exhaustive googling, searching, and reading, I'm still unable to get mldonkey-server to run on it's own as a daemon/service or however you like to call it. My knowledge of linux system stuff is ver poor and I find myself unable to solve this issues, and I don't really know what kind of information you might need in order to help me out. Please ask right away and I'll tell you what you need.

What I'd like to get after all is:
* Install mldonkey-server into a standard system location.
* Have mldonkey-server use a work folder outside my home folder (/var/mldonkey ?).
* Be able to use a gui like KMLDonkey from any of my user accounts to manage the core.
* Have mldonkey-server running all the time, behind the scenes.
* Have mldonkey-server start at system startup, not at user login or else.

I have basic linux knowledge. Just enough to break my system accidentally (happened 2 month ago) and to delete my home folder (also happened 2 weeks ago), and I feel comfortable using the shell.

I thank you for the time you've spent reading this, and I hope some person is able to give me advice in order to get this done.

---

### Post by tbroderick on 2006-12-16
mldonkey-server, mldonkey-gui and kmldonkey are all in the universe repo. You can just install them through synaptic, aptitude or apt-get once you enable the repo.


[https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

---

### Post by chrishoeppner on 2006-12-17
Thank you for your kind reply. Please note, as I stated above, that I already installed mldonkey-server with apt-get. At this point it's running, still I'm unable to import my tempfiles from my compiled mldonkey-server install. Plus it does not run at startup, but I remember reading about a patch, although I can't remember where.

Does anyone know how I can import the mldonkey temps from one install to another? Moving them into the new temp folder did not work.

Thanks everyone!

---

### Post by Lunks on 2007-07-03
I'm interested in doing the same thing: keeping mlnet running on the background. But I've got no idea on how to do it. Any help, please?

---

### Post by yakkeh on 2007-12-24
try 

sudo dpkg-reconfigure mldonkey-server

This command, dpkg-reconfigure, will reconfigure your mldonkey settings. It gives you the option to start mldonkey-server at system startup... say YES. Some other options are presented like upload/download speeds you will allow it and the nice value (man nice).

Otherwise, if you want to manually run mldonkey in the background... 
nohup mlnet & > /dev/null &

Also check out [http://mldonkey.sourceforge.net/Main_Page](http://mldonkey.sourceforge.net/Main_Page)

---

