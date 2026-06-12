---
title: "Automatix2"
date: 2007-03-15
forum: Absolute Beginner Talk
---

### Post by familyjules74123 on 2007-03-15
can anyone point me in the direction of a howto to install automatix, i checked the automatix website but the wiki is down as of yesterday.

---

### Post by oilchangeguy on 2007-03-15
you'll need to wait until the website is available. even if you could somehow install it , you can't run it if the website is down.

---

### Post by familyjules74123 on 2007-03-15
the website isnt down (sorry for not specifying) its just wiki that is down, they just switched servers and havent moved everything yet i suppose.

---

### Post by daradib on 2007-03-15
Edit your sources.list
Enter following in terminal:
[I]sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list[/I]

Add the following:
```
#Automatix2
deb http://www.getautomatix.com/apt/ edgy main 
```

Save and exit

Enter following in terminal:
[I]sudo apt-get update
sudo apt-get install automatix2[/I]

Open Automatix2 via System -> Automatix Graphical Installer Script for Ubuntu/Kubuntu

---

### Post by cgdoc7 on 2007-03-16
> **daradib said:**
> Edit your sources.list
Enter following in terminal:
[I]sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
sudo gedit /etc/apt/sources.list[/I]

Add the following:
```
#Automatix2
deb http://www.getautomatix.com/apt/ edgy main 
```

Save and exit

Enter following in terminal:
[I]sudo apt-get update
sudo apt-get install automatix2[/I]

Open Automatix2 via System -> Automatix Graphical Installer Script for Ubuntu/Kubuntu

Works perfect, thanks!

---

### Post by familyjules74123 on 2007-03-16
yeah i got it to work.

---

### Post by noob_saioke45601 on 2007-03-16
didnt work for me... after i typed sudo apt-get update i got this error.

"W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems"

any answers?

---

### Post by dimis on 2007-03-16
Problem with key here too:
```
 sudo automatix2

(automatix.py:5057): libglade-WARNING **: unknown property `wrap_mode' for class  `GtkLabel'
Starting
could not create keys directory
--17:48:05--  http://www.getautomatix.com/keys/quinn1.key
           => `quinn1.key'
Resolving www.getautomatix.com... 208.113.170.63
Connecting to www.getautomatix.com|208.113.170.63|:80... connected.
HTTP request sent, awaiting response... 404 Not Found
17:48:06 ERROR 404: Not Found.

```
But it is reasonable that I have a 404 error, since if you visit [http://www.getautomatix.com/keys/]("http://www.getautomatix.com/keys/") you 'll realize that quinn1.key does not exist.

Any ideas on fixing this? I tried to check automatix2 and automatix.py, but none of them had a direct reference so that I can change it and try one of the other keys online.

Any help is really much appreciated!

---

### Post by silkstone on 2007-03-16
I think this key problem has been mentioned in another thread. This should solve it...

If you're using Automatix and are getting a 'Not Authenticated' warning or an error saying that a key cannot be found when you try to update...

1. wget http ://www.getautomatix.com/keys/automatix2.key
(without the space after http)

2. gpg --import automatix2.key

3. gpg --export --armor E23C5FC3 | sudo apt-key add -

That should restore the key.

---

### Post by daradib on 2007-03-16
> didnt work for me... after i typed sudo apt-get update i got this error.

"W: GPG error: [http://www.getautomatix.com](http://www.getautomatix.com) edgy Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY CC919A31E23C5FC3
W: You may want to run apt-get update to correct these problems"

Yeah, later I realized about the GPG error. However, you can still work with the GPG error with no problems (with no issue except for a warning at sudo apt-get update and when installing).  You can still install with the warning.

---

### Post by noob_saioke45601 on 2007-03-16
your right. thanks got it installed.

---

### Post by familyjules74123 on 2007-03-17
anyone having any problems with any of the programs they installed with automatix? my direct connect client installed does not work.

---

### Post by jackrobinson on 2007-03-17
> **familyjules74123 said:**
> anyone having any problems with any of the programs they installed with automatix? my direct connect client installed does not work.
I tested it and it works.. do this:
```
sudo apt-get update
sudo apt-get upgrade
```
Now you will have the latest automatix2. 
Run it and **uninstall** DC++
and then **reinstall** it. It will work after that.

---

### Post by dimis on 2007-03-18
> **silkstone said:**
> I think this key problem has been mentioned in another thread. This should solve it...

If you're using Automatix and are getting a 'Not Authenticated' warning or an error saying that a key cannot be found when you try to update...

1. wget http ://www.getautomatix.com/keys/automatix2.key
(without the space after http)

2. gpg --import automatix2.key

3. gpg --export --armor E23C5FC3 | sudo apt-key add -

That should restore the key.
The point is that automatix will still try to find quinn.key. So, why would this thing work for me? (I am also implying that I tested it and it doesn't work)

Thanks though for the try,
 - d

---

### Post by jackrobinson on 2007-03-18
> **dimis said:**
> The point is that automatix will still try to find quinn.key. So, why would this thing work for me? (I am also implying that I tested it and it doesn't work)

Thanks though for the try,
 - d

Thats why you need to update automatix to the latest version..
```
sudo apt-get update
sudo apt-get upgrade
```

---

### Post by girard on 2007-03-19
> **silkstone said:**
> I think this key problem has been mentioned in another thread. This should solve it...

If you're using Automatix and are getting a 'Not Authenticated' warning or an error saying that a key cannot be found when you try to update...

1. wget http ://www.getautomatix.com/keys/automatix2.key
(without the space after http)

2. gpg --import automatix2.key

3. gpg --export --armor E23C5FC3 | sudo apt-key add -

That should restore the key.
hi. i did eveything on this thread and it worked fine. thanks a lot. i do however have a question as to what all these commands do? what is gpg, etc... i'm just starting to learn about linux and i'd also like to know what these things mean... not just to make my system work fine. thanks.

---

### Post by tinyneutrino on 2007-03-19
I just install Automatix and had no problems following the instructions at the website. It worked like a charm, although I had to go through a dpkg-reconfigure -a   about four times before I could get my update working right again. Finally fixed everything through Synaptic - rebooted and everything worked like a charm.

One strange thing has happened. My Synaptic at 'Settings-Repositories' = brings up the 'Properties' window, in 'Properties' as well. Weird.  Haven't figured this one out yet.

While doing the Automatix, I also found a neat way to install Internet Explorer  ([http://www.tatanka.com.br/ies4linux/page/Main_Page]("http://www.tatanka.com.br/ies4linux/page/Main_Page") )    that works fine on Ubuntu. I know, why would I want it........  Well, its not my machine, and, there are still a few commercial sites that only work on Window$ Internet Exploder.  On the other hand, now I have a Win program that works on Linux, while Window$ won't handle any Linux applications.....

---

### Post by charles.g.moore on 2007-03-19
> **silkstone said:**
> I think this key problem has been mentioned in another thread. This should solve it...

If you're using Automatix and are getting a 'Not Authenticated' warning or an error saying that a key cannot be found when you try to update...

1. wget http ://www.getautomatix.com/keys/automatix2.key
(without the space after http)

2. gpg --import automatix2.key

3. gpg --export --armor E23C5FC3 | sudo apt-key add -

That should restore the key.

This worked perfect for me thank you...

---

### Post by daradib on 2007-03-19
> hi. i did eveything on this thread and it worked fine. thanks a lot. i do however have a question as to what all these commands do? what is gpg, etc... i'm just starting to learn about linux and i'd also like to know what these things mean... not just to make my system work fine. thanks.

GPG (or GnuPG) allows one to encrypt and sign data and communication. See [http://www.gnupg.org/](http://www.gnupg.org/) for more information. Repositories have keys so that the repository is digitally signed. I believe this is useful for mirrors of repositories, to show that the software has not been tampered with (you wouldn't want someone to have a tampered mirror of a repository that gives you potentially some kind of malware (virus, trojan horses, worms, etc.).

Those commands download the repository key and add it to GPG's list of keys so that it can be made sure you are receiving an original (not tampered with) copy of software.

Correct me if I am wrong.

---

