---
title: "Newb. Question about installing programs"
date: 2007-02-02
forum: Absolute Beginner Talk
---

### Post by rew on 2007-02-02
hi. this is my second day using ubuntu and I downloaded thunderbird for firefox. my question is how do I install it?

---

### Post by shareMenaPeace on 2007-02-02
Try using the synaptic package manager to install thunderbird(mozilla).
Go to System -> Administration -> Synapptic Package Manager start it and type into the searchbox "thunderbird" than you should see it and can checkbox enable it, "apply" installs it and adding an "Application" Shortcut.

---

### Post by Jive Turkey on 2007-02-02
I think you are in luck, in that you dont even need that file you downloaded.  open a terminal and type ```
sudo apt-get install thunderbird
```

trust me its way easier than installing by hand, even if the instuctions are present and make logical sense.

---

### Post by bscbrit on 2007-02-02
How did you download it. As a .deb, .tar.gz or using Synaptic - which will install it automatically for you?

---

### Post by Maestro23 on 2007-02-02
Good link for new people: [http://ubuntuguide.org/wiki/Ubuntu_Edgy](http://ubuntuguide.org/wiki/Ubuntu_Edgy)

---

### Post by rew on 2007-02-02
i tried both of those and couldn't get it to work. i downloaded it with the "archive manager" as a tar.giz. :confused:

---

### Post by rew on 2007-02-02
Package mozilla-thunderbird is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source


i keep getting this message

---

### Post by dstew on 2007-02-02
rew, what kind of ubuntu do you have installed?

---

### Post by rew on 2007-02-02
6.10? its the newest version

---

### Post by bscbrit on 2007-02-03
OK, what I would suggest is that you open Synaptic, (System->Administration->Synaptic Package Manager) and open the repository editor.  Make sure that you have selected all the repos as active.  Once you have done that and closed the editor window, select Reload in Synaptic.  When it has completed its update you should be able to search for mozilla-thunderbird,  then select it and click on Apply.  If at any time Synaptic complains it is probably a corrupt installation.  All the package managers rely on the same software underneath their GUIs and it is important that you get a working package manager.  If you have any problems, or more questions, then please come back here.

---

### Post by jvc26 on 2007-02-03
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Email_Client_.28Mozilla_Thunderbird.29](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_Email_Client_.28Mozilla_Thunderbird.29)
to install thunderbird
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
on installing just about everything
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_add_extra_repositories)
if you dont know how to add extra repos.
Il

---

