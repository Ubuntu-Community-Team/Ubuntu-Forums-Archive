---
title: "Install Java using .deb package"
date: 2007-05-27
forum: Absolute Beginner Talk
---

### Post by noorez on 2007-05-27
When I installed java before I used a method described in another post by using the update-alternatives once the .bin package was executed and the file moved to the appropriate location. However, I would like to do it so that all executables in the bin directory of the Java folder are ready to use. I read on a website tutorial that creating a .deb package would work, but I can't figure out how to do this. Can I get help with this?

---

### Post by kerry_s on 2007-05-27
Just open synaptic and do a search for sun-java, make sure all your repo's are on, then just click on it to mark for installation. There are 21000+ applications in the repos, you should always check there first.

if you can't find it in the menu
Press alt+F2 type> gksu synaptic

---

### Post by noorez on 2007-05-27
Installing java using what is already in repos seems to require various packages. I think I would rather have everything together so that when Sun comes out with a new Java version or update I can just remove the old and install the new.

---

### Post by kerry_s on 2007-05-28
Well yes, java has dependency's to run, if you compile it yourself it will require alot more than that, you will need all those dependency's plus the build-essential package and i'm sure there's more, but i don't know what.

---

### Post by noorez on 2007-05-28
It doesn't seem to require much?.....I am using the .bin installer from the SUN website. When I was doing it before I just ran the .bin file to extract the contents, moved it into the /usr/lib directory and then used update-alternatives to all the programs in the JDK bin directory. I checked and all the dependencies that would have been used had I downloaded from a repos were not being used. I am not actually compiling anything my self.

---

### Post by kerry_s on 2007-05-28
Okay, what ever works for you. Can you post a link to the java your trying to install, it might help if we could see it, download it and read the readme file to help you with the setup.

---

### Post by noorez on 2007-05-29
Sun Website:

 [http://java.sun.com/javase/downloads/index.jsp](http://java.sun.com/javase/downloads/index.jsp)

I did a bit of experimenting and looked int he .deb file for the java installation from the repos and took a look at the script files which I used to create my own for installation and removal. The only thing that my script does is do the update-alternatives installation and removal.

---

### Post by zvacet on 2007-05-29
Take advice that kerry_s give to you and install Java from repos.Belive me it is easyest way to do it.

---

