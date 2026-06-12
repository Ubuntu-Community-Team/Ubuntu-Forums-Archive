---
title: "A few simple questions (my first experience with ubuntu)"
date: 2007-11-13
forum: Absolute Beginner Talk
---

### Post by i0ls on 2007-11-13
allright this is my first time running ubuntu after some light experience with fedora, and gentoo.

i am use to being able to login at the login screen with a root account and have privileges to change what i want or copy files to wherever. i was met at the login screen with (root cannot login here) message. how can i get privileges to say copy files to /usr. i know su - but its been about 4 years since i ran a linux environment and i am tripping over my own feet in the console.

once i am in the console i am use to being able to hit tab and auto complete file names, ect.  tab now makes the pc beep. is there's something i can set up somewhere for auto complete with tab?

i was just running fc8 and rythmbox had the ability to play mp3. is the rythmbox shipped with ubutnu not able to play because its what is shipped with the os? i know about licensing  and hopefully i am just missing a package or plugins.

how does ubuntu handle packages from the console? lets say for example i want to remove and reinstall rythmbox and hope it plays mp3's. 

the first time i booted i went on firefox and googled ubuntu and the word mp3 click on the first link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ok system/add remove and search for xubuntu-restricted-extras and add the package. there's an error loading the package and i can no longer read the packages on the machine and or update or change any of them. back to live cd for another install. question being is ubuntu that gentle of an os where if there's a problem installing a packing i am going to have to start over again? or were those just 3rd party packages that corrupted things for a lack of better terms?

---

### Post by ddrichardson on 2007-11-13
> **i0ls said:**
> allright this is my first time running ubuntu after some light experience with fedora, and gentoo.

i am use to being able to login at the login screen with a root account and have privileges to change what i want or copy files to wherever. i was met at the login screen with (root cannot login here) message. how can i get privileges to say copy files to /usr. i know su - but its been about 4 years since i ran a linux environment and i am tripping over my own feet in the console.Ubuntu doesn't enable the root account by default it uses sudo instead.

> **i0ls said:**
>  once i am in the console i am use to being able to hit tab and auto complete file names, ect.  tab now makes the pc beep. is there's something i can set up somewhere for auto complete with tab?Autocomplete works in Ubuntu, the beep indicates there is nothing to complete or there are more choices, try hitting tab twice and you should get a list of commands that are similar.

> **i0ls said:**
>  i was just running fc8 and rythmbox had the ability to play mp3. is the rythmbox shipped with ubutnu not able to play because its what is shipped with the os? i know about licensing  and hopefully i am just missing a package or plugins.Just install the plugins from add/remove software.

> **i0ls said:**
>  how does ubuntu handle packages from the console? lets say for example i want to remove and reinstall rythmbox and hope it plays mp3's.aptitude - ```
sudo apt-get install packagename
sudo apt-get remove packagename
```

> **i0ls said:**
>  the first time i booted i went on firefox and googled ubuntu and the word mp3 click on the first link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ok system/add remove and search for xubuntu-restricted-extras and add the package. there's an error loading the package and i can no longer read the packages on the machine and or update or change any of them. back to live cd for another install. question being is ubuntu that gentle of an os where if there's a problem installing a packing i am going to have to start over again? or were those just 3rd party packages that corrupted things for a lack of better terms?What was the error message you encountered, they are usually resolved using dpkg.

---

### Post by Inxsible on 2007-11-13
> **i0ls said:**
> allright this is my first time running ubuntu after some light experience with fedora, and gentoo.

i am use to being able to login at the login screen with a root account and have privileges to change what i want or copy files to wherever. i was met at the login screen with (root cannot login here) message. how can i get privileges to say copy files to /usr. i know su - but its been about 4 years since i ran a linux environment and i am tripping over my own feet in the console.

once i am in the console i am use to being able to hit tab and auto complete file names, ect.  tab now makes the pc beep. is there's something i can set up somewhere for auto complete with tab?

i was just running fc8 and rythmbox had the ability to play mp3. is the rythmbox shipped with ubutnu not able to play because its what is shipped with the os? i know about licensing  and hopefully i am just missing a package or plugins.

how does ubuntu handle packages from the console? lets say for example i want to remove and reinstall rythmbox and hope it plays mp3's. 

the first time i booted i went on firefox and googled ubuntu and the word mp3 click on the first link [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats) ok system/add remove and search for xubuntu-restricted-extras and add the package. there's an error loading the package and i can no longer read the packages on the machine and or update or change any of them. back to live cd for another install. question being is ubuntu that gentle of an os where if there's a problem installing a packing i am going to have to start over again? or were those just 3rd party packages that corrupted things for a lack of better terms?
you can copy files using the following command:
```
sudo cp /path/to/copy/from /path/to/copy/to
```

Rhythmbox, nor any other player for that matter will play mp3 etc because of Ubuntu's policy that no proprietary software is installed by default. You can however install them and then everything works.

removing and re-installing rhythmbox will not help unless you also install the missing plugins for mp3 support etc.

---

### Post by Pumalite on 2007-11-13
[http://www.linux-tutorial.info/index.php](http://www.linux-tutorial.info/index.php)
[http://www.linux.org/lessons/beginner/toc.html](http://www.linux.org/lessons/beginner/toc.html)
[http://howtoforge.com/taxonomy_menu/1/1/50](http://howtoforge.com/taxonomy_menu/1/1/50)
[http://www.littleigloo.org/tutorial.php3](http://www.littleigloo.org/tutorial.php3)
[http://www.geekgirls.com/](http://www.geekgirls.com/)
[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by i0ls on 2007-11-14
wow, thanks for the replys and advice and links. i am trying to get on my feet in terms of bieng almost competent in the os and completely abandon windows free of terrible experiences.

---

