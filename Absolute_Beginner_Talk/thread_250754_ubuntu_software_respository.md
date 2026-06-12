---
title: "ubuntu software respository"
date: 2006-09-04
forum: Absolute Beginner Talk
---

### Post by adamstar on 2006-09-04
Where is the respository?...does it have a url?

Adam

---

### Post by 3rr0r on 2006-09-04
if you are referring to the universe and multi-verse, you can add these to your box by going to :

System > Admin > Software Properties 

Click Add, select universe and multiverse, then hit apply or Ok or whatever it is  :rolleyes:   

Then when you go into synaptic.... there will be a ton more software at your disposal.  Viva la revolucion!

Hope that is what you wanted.

---

### Post by b_martinez on 2006-09-04
Are you just wanting to see what there is to install? If so, start Synaptic or Kpackage. If not, let us know what you want to do, please.
Bill

---

### Post by JNowka on 2006-09-04
If you Linux computer can connect to the internet then I suggest going to System->Administration->Synaptic Package Manager.  Once there you can goto Settings->Repositories and choose the ones you want, and add to them.  The packages avalible in the repositorie will show up in the catagories to the right as unfilled white boxes.  If you see something you like click on the box and select Mark for Installation.

If you do not have the internet on your Ubuntu computer you can take a longer, more headachie way to get programs installed.  This will require either a cd writing drive on another computer that has the internet and alot of time on your behalf, or a network connection between the two computers.  You will have to goto "packages.ubuntu.com" to download the programs you want, and all of its dependencies(this can be many).  The dependencies even have dependencies many times.  once done access the CD/Network folder via the terminal/konsole and type "sudo dpkg -i *.deb" this will install all the programs and tell you if something cant be installed because of dependencies problems, meaning go back and download somemore fun stuff.

---

