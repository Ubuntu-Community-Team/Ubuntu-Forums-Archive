---
title: "Synaptic Package Mgr/apt-get/Update Mgr"
date: 2006-01-06
forum: Absolute Beginner Talk
---

### Post by PlatinumPlus on 2006-01-06
Is there a way of getting any one of these apps (Synaptic Package Manager/apt-get/Update Manager) to save a local copy of what I would have downloaded so that I can update an offline machine? I have seen that Synaptic Package Manager copies to a cache then deletes it. 

In Preferences I have selected the option - Leave all downloaded packages in the cache - but maybe there is another cache it is saving in. I did a search for the file as it was being downloaded but I could only see it via the console and the text was red. :rolleyes:

---

### Post by Perfect Storm on 2006-01-06
take a look in 

/var/cache/apt/archives

---

### Post by PlatinumPlus on 2006-01-06
I have done an install of 3DChess and the file has been successfully saved in that folder :KS 

 but there is not icon/shortut for it.  :confused: 

Also now I am assuming I do the following:

I copy the files in the /var/cache/apt/archives folder to my offline machine.
I customise my repository to match where I have copied the files
Then I do an install from Synaptics and it should similarly install on the offline pc?

---

### Post by estel on 2006-01-06
You need to use the dpkg command... Can't remember the syntax for it though

---

### Post by TeeAhr1 on 2006-01-06
If you put the folder in the repository list, you should simply be able to do a search withing Synaptic (ctrl-f) for 3dchess and install it as you normally would.

---

### Post by carlosqueso on 2006-01-06
[QUOTE=estel]You need to use the dpkg command... Can't remember the syntax for it though[/QUOTE]

It's ```
sudo dpkg -i <name of the deb file that you're installing>
```

of course, omit the angle brackets.

Incidentally, you'll be able to remove the packages with the normal apt/synaptic way.

---

### Post by PlatinumPlus on 2006-01-09
I tried using dpkg to install supertux but ti told me I needed to install
libsdl-mixer1.2_1.2.6-1.1_i386.deb and libsdl-image1.2_1.2.4-1_i386.deb first which I did but when I tried supertux-data_0.1.2-4ubuntu1_all.deb and supertux_0.1.2-4ubuntu1_i386.deb it kept on saying I had to install supertux-data first :confused: 

For MySQL, when I installed on the online machine I was asked to insert the Install disk which I did and it setup no problem. For the offline pc, how do I get it to do this since it tells me I need mailx and some other files it depends on to run. I even tried dselect but I ended up confused because I could not specify my own path to the deb files. :rolleyes:

---

### Post by PlatinumPlus on 2006-01-11
I have come across apt-cacher and it seems to be what the doctor ordered. What I am not sure of now is since it also has dependencies how will I set it up on the offline machines or is it only required on the pc which is caching? I am only coming across documentation which explains what it can be used for but not how it is done.

I have my *.deb files sitting in /var/cache/apt/archives which I will test with and see how much I can cover.

---

