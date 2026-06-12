---
title: "adobe flash player"
date: 2007-02-09
forum: Absolute Beginner Talk
---

### Post by thebes on 2007-02-09
i am trying to make sense of these instructions but seeing as it is one of the first times it is proving to be rather "irritating"
I could not install the flash player automatically. i gave me some sort of error 
  > 1.  Click the "Download .rpm" link. A dialog box will appear asking you where to save the file. 
done 
  > 2. Save the .rpm file to your desktop and wait for the file to download completely. 
done 
> 3. In terminal, navigate to the desktop and type # rpm -Uvh <rpm_package_file>. Click Enter. (Note: This must be done as a root user). The installer will instruct you to shut down your browser(s). 
  
so i am assuming that i am on the desktop, because on the terminal i can see "username-desktop:$". so now i type the first part of the code "# rpm -Uvh" and not sure about the second part either verbatim or the name of the file and nothing happens :confused:  

   > 4. Once the installation is complete, the plug-in will be installed in your Mozilla browser. To verify, launch Mozilla and choose Help > About Plug-ins from the browser menu.

---

### Post by finer recliner on 2007-02-09
rpm are red hat installers. ubuntu is based on debain. (red hat and debian are both other linux flavors). in the future, look for .deb installers. in this case, i think you can just download the source code and compile it yourself.

---

### Post by gh0st on 2007-02-09
Hi, are these the instructions from the Adobe site? I'm guessing they are.

Anyway, .rpm files are not used on Ubuntu they are for versions of Linux based on the Red Hat distribution usually, Ubuntu is based on Debian and we use .deb binary files, thats what the Add/Remove programs tool and all other package managers on Ubuntu use.

There are ways to convert .rpm to .deb if you really need to but it's not relevant in this case I don't think.

I found this thread that you might wanna try, it was posted by someone with the same problem and seems to have solved it for them. You should be able to find the answer here I think.

[http://www.ubuntuforums.org/showthread.php?t=353952](http://www.ubuntuforums.org/showthread.php?t=353952)

Hope that helps, if you need anything else let me know :)

---

### Post by thebes on 2007-02-09
thanks for the info. i ll have to give this a thorough look once i come back from school 
i shouldnt have read the "Absolute Beginner Talk rules" seeing as how any question can be asked without being yelled at and how i am lazy i tend not to search too much ;)

---

### Post by Maestro23 on 2007-02-09
> **thebes said:**
> thanks for the info. i ll have to give this a thorough look once i come back from school 
i shouldnt have read the "Absolute Beginner Talk rules" seeing as how any question can be asked without being yelled at and how i am lazy i tend not to search too much ;)

These boards are full of help and good people.  Don't be afraid to ask or search for answers.  This link might help you out in the long run: [http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)

---

### Post by thebes on 2007-02-09
thanks for everything guys. it worked. and the link is in my bookmarks

---

### Post by -Ghost9- on 2007-02-09
here's what i don't get about the whole flash player thing. In FF2 i went to a site that had flash, it prompted me to install a plugin and I clicked ok. vwalla I'm done. Now flash works just fine on my system.  Where's the complicatedness?

---

### Post by gh0st on 2007-02-09
> **-Ghost9- said:**
> here's what i don't get about the whole flash player thing. In FF2 i went to a site that had flash, it prompted me to install a plugin and I clicked ok. vwalla I'm done. Now flash works just fine on my system.  Where's the complicatedness?

Yeah nowadays it is pretty easy but until recently you had to install the Flash 9 Beta on Linux and it wouldn't prompt you to do that through Firefox or on the Adobe site. You had to install it by getting the Tarball and copying the files to the appropriate system locations. Not always trivial if you are a new user.

The problem basically stems from the fact that Adobe didn't release a Flash Player 8 for Linux and we were stuck on 7. Some of the video from sites like YouTube was encoded in Flash 8 and wouldn't work with 7, so Linux users were stuck with Flash 7 for a long time. It wasn't until Adobe started developing Flash 9 they thought "we should make this for Linux as well".

Some people used to install the Windows version of Firefox through WINE and then install the Windows Flash plugin for it, just to watch videos in Flash and stuff. I never bothered but it did used to annoy me quite a bit I couldn't watch the links people sent me. You would just get errors saying "newer version of Flash required" when you loaded a page because they were designed to look for Flash 8 and we didn't have a Flash 8. Most developers only cared about Mac and Windows anyway it seems.

As I said earlier, Firefox and the Adobe site would just say you had the latest version of Flash if you had 7 even when the beta of Flash 9 was out and worked perfectly from what I saw of it. In short, there was a big problem and there is still a hangover from it, I think the release of Firefox 2 might have helped the situation as well in some way but I'm just speculating there.

That's bit of a long winded explanation but hopefully it makes sense :)

---

### Post by thebes on 2007-02-10
> **-Ghost9- said:**
> here's what i don't get about the whole flash player thing. In FF2 i went to a site that had flash, it prompted me to install a plugin and I clicked ok. vwalla I'm done. Now flash works just fine on my system.  Where's the complicatedness?


it gave me an error and told me to install it manually. tried a bunch of times

---

### Post by gh0st on 2007-02-10
> **thebes said:**
> it gave me an error and told me to install it manually. tried a bunch of times

Yeah thats what happened to me loads of times, I was surprised when I heard someone had done it that way. Really though if Linux is gonna be a serious home users desktop it needs to be able to do things like this.

What version of Firefox do you use? I have 2.0 but I already had Flash installed when I upgraded from 1.5, that's why I was wondering if there was some change in 2.0 that made this process easier if Flash wasn't installed already. It would be cool if there is.

---

