---
title: "add/remove.. download only"
date: 2007-09-11
forum: Absolute Beginner Talk
---

### Post by Lelouch on 2007-09-11
When i install programs using add/remove or synaptic, i can check the (download only) box so then it won't be installed...

i want to install the packages manually, but where are they downloaded? i mean, the location?

---

### Post by Yes on 2007-09-11
When you use Synaptic, you should be able to right click on the check box and choose "Install".  When you click the apply button, that prackage should be downloaded and installed.

Your other option is to use "apt-get install *your package*".

---

### Post by Lelouch on 2007-09-11
I know that... but i dont want to install the package, i just want to dl it

so i checked that box, but where is it stored?

---

### Post by Yes on 2007-09-11
I'm not sure, I didn't even know that you could only download the package.

You can download the tarball for the program [here](http://packages.ubuntu.com/), so that way you'll know where you're downloading it.

---

### Post by sawjew on 2007-09-11
I'm not sure because I have never used the download only feature but have you checked ```
/var/cache/apt/archives
```

That's where synaptic arhives anything you install, everything's downloaded to there anyway.

Just a question, why do you want to download only? :confused: If you want to save the package for later it's in /var/cache/apt/archives anyway and if you really want to keep your packages or use them on another system you can use APTonCD to copy everything from /var/cache/apt/archives to a cd and set it up as a repository.

---

### Post by Anicka on 2007-09-11
Use the command "sudo apt-get -d install <your packages>" The -d flag means "download only, no install". The files will end up in the normal place (/var/cache/apt/archives). Or you can use "sudo aptitude download <packages>" and the deb-files will end up at your current location. (I wasn't able to find that command for apt-get, but I know it works in aptitude.)

---

### Post by Lelouch on 2007-09-11
yes.. found them there.. thanks..

about aptoncd, i dont like it....

i didnt know that the packages (even after installing) are stored there... this will help me alot

thanks

---

### Post by mlentink on 2007-09-11
Still, you haven't exactly answered the question why you would want to do this in the first place. 
I'd really be interested to know. Why use your own storage when those packages are available in repositories?

---

### Post by Lelouch on 2007-09-11
i will move soon to another country, where the internet is TOO slow... and i dont think i will redownload all my appliactions if i had to reinstall ubuntu...

---

### Post by mlentink on 2007-09-11
Thx, fair enough. I should know better than to assume fast internet access is everywhere.....

---

