---
title: "downloaded packages. where do they go?"
date: 2006-11-21
forum: Absolute Beginner Talk
---

### Post by camilluk on 2006-11-21
When using Synaptic, where do the downloaded packages go? I can't find them, but that could be just me... so I'd rather ask the question.

And are they left in their destination after they are installed or do they get deleted by Synaptic?

If they are still there, I copy them, put them in the same place after a full reinstall, and use the 'install downloaded packages' (or something like that...) item on the menu, will Synaptic be able to figure out all the dependencies or, since it hasn't done its own downloading, will it just install the debs it finds?

I'm asking these questions because I have now been messing around with Ubuntu/Kubuntu for a while and have learned how I could have configured my machine better, so I would like to reinstall from scratch (changing the way I partitioned my HD and everything), but I would like to avoid downloading again all the packages I downloaded already and that I know I will want in the new install. Apart from the questions above, any suggestions on how to achieve this are welcome!

Thank you anyone!
Cam

---

### Post by Jimmey on 2006-11-21
When you use Synaptic, the packages that you download go to /var/cache/apt/.

From there, they're (usually) installed automatically.

If you just backup /var/cache/apt, then you should be good to go.

A word about the installation of these packages after your reinstall, though:

If you backup /var/cache/apt/, you might just want to backup the "apt" folder. If you then replace the new install's /var/cache/apt with the one you've backed up, and type > sudo dpkg -i $(ls/var/cache/apt/*.deb)
Then it should install every package that's in there.

---

### Post by deadgobby on 2006-11-21
They can most likely can be found in 
places>Home Folder>File System> Usr folder.

---

### Post by adwait on 2006-11-21
The downloaded packages are stroed @ /var/cache/apt/archives. They are periodically cleaned out by synaptic (I think).

IF you copy all the files over there into a CD, and you want to reinstall all those updates, after you reinstall Ubuntu, just copy them back to that location. After that, you can run 
```
sudo apt-get upgrade
```

This will work fine, in case all that is there are upgrades. But if you have installed packages which aren't there in Ubuntu in the first place, then those won't get installed. To install those, you would have to use
```
sudo dpkg -i /var/cacje/apt/archives/*.deb
```

This command will only install those packages if the dependencies are met, if not it will give an error. It can't download the dependencies automatically. Also, you might want to run this command again and again even if it gives dependency errors because the command will install alphabetically so if a pacakage beginning with a requires a package beginning with z to be installed, it will give an error in the first try but will install in the 2nd try.

---

### Post by Ben Sprinkle on 2006-11-21
If you ever want to delete all of the crap you downloaded and don't feel like doing rm *.deb just do this:
```

sudo apt-get clean

```
It will remove all of the downloaded packages but not uninstall them.

---

### Post by camilluk on 2006-11-21
Thank you guys! I'll give it a try! :D

---

### Post by camilluk on 2006-11-21
Just thinking... and what if I put those packages on a cd, or on a specific folder and then add this cd/folder to my sources list (temporarily). If I then

```
sudo apt-get update
```and mark the packages I want from Synaptic and install, would it work?

The thing is, I don't want to

```
 sudo dpkg -i /var/cacje/apt/archives/*.deb
```because it would likely install things I don't want. My proposed method (if it worked) would avoid having to pick and chose every single deb, bin or whatever, paying attention to which ones give error, which ones are proper apps and which ones are libraries, while in Synaptic all I have to mark is the main package and it would resolve the dependencies by itself.

Give me a slap if I'm not making sense. I'm just very lazy ;)...

---

### Post by adwait on 2006-11-21
Why do you think dpkg -i *.deb would install a lot of unnecessary things? It would only install the things that you have downloaded and installed currently.

You can do what you are saying because, you would need an entire mirror on the CD to be able to do that. ie: now just the packages you downloaded, but EVERYTHING thats in the Ubuntu repos. Also, even if you did do that (on a DVD), there would be no way for Synaptic to know what you installed and what you didn't before. What you could do though is, copy the deb files in the /var/cache/apt/archives and then in synaptic, select the packages you want to install. It will detect the packages that are already present on the disk and will only download those which are not on the disk. But in this method, you need to know what you want to install ie: it can't automatically know what you had installed and what you hadn't by looking at the files in /var/cache/apt/archives.

---

### Post by camilluk on 2006-11-22
> Why do you think dpkg -i *.deb would install a lot of unnecessary things? It would only install the things that you have downloaded and installed currently

because I downloaded and installed more things that I need and I don't want to clutter my new install. I know the things I want to reinstall, I just didn't want to download them once more.

Thank you for your help!
Cam

---

