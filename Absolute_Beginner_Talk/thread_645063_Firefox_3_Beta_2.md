---
title: "Firefox 3 Beta 2"
date: 2007-12-19
forum: Absolute Beginner Talk
---

### Post by KudoKid on 2007-12-19
I downloaded the folder but without instructions im clueless on theses things.
Is the a generic way of installing these things or is it different with all the other things not on the add/remove programs list?

Any help is great, thanks a ton. =)

---

### Post by LaRoza on 2007-12-19
In Synaptic, search for "firefox-granparadiso". It can be safely added and removed.

```

sudo aptitude install firefox-granparadiso

```

---

### Post by Lord_Dicranius on 2007-12-19
What's the name of the file that was downloaded?

If you're able to unpack the file (if it came as a .tar, .tar.gz, etc), is there a README file in there?  That might include instructions on how to install it.

**EDIT**
Ooh, didn't know it was in the repo's.  Thanks LaRoza :)

---

### Post by zvacet on 2007-12-19
```
tar jxvf packagename.tar.bz2
cd /packagename_folder
```

Packagename is exact name of your program(firefox in this case)


You will find there **install** and **read me** file.Read them and you will know what to do.

---

### Post by KudoKid on 2007-12-19
In searching the synaptic thing i only found alpha 8. =/

---

### Post by misfitpierce on 2007-12-19
Should be alpha8 or 9 and granparadiso

---

### Post by climber117 on 2007-12-19
Don't know what folder you're referring to, but here's how I did it. Grab the beta from [http://www.mozilla.com/en-US/firefox/all-beta.html]("http://www.mozilla.com/en-US/firefox/all-beta.html"). Download the file for Linux for your language. You'll download a tar archive. Extract it (right-click and hit "Extract here"). Doesn't matter where you extract it. Open a terminal and cd to the folder where you extracted it. Then: ```
sh firefox
``` That should run the beta version of Firefox. Do not close the terminal, or Firefox will close too. Firefox will probably disable all your extensions and themes, but when I went back to Firefox 2, it had automatically re-enabled them. Hope this helps.

---

### Post by sicofante on 2007-12-21
I don't know what's going on but when I launch the beta version I always get the old version 2 running. I've tried running ./firefox and sh ./firefox on the downloaded folder to no avail.

I'm running Xubuntu on an old laptop and everything else seems fine.

Any ideas?

EDIT: There's no readme or install file in the tar archive.

---

### Post by Old Pink on 2007-12-23
> **KudoKid said:**
> In searching the synaptic thing i only found alpha 8. =/If you have that package installed, this guide should help you update the alpha to the most recent BETA.

[http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710](http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710)

---

### Post by Epilonsama on 2007-12-23
> **Old Pink said:**
> If you have that package installed, this guide should help you update the alpha to the most recent BETA.

[http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710](http://www.topicalmatt.com/23-12-2007/firefox-3-beta-2-in-ubuntu-710)

I tried this but when u type firefox-3.0 or click on the menu link, it says :
> home@linuxmint:~$ firefox-3.0 %u
bash: firefox-3.0: command not found


---

### Post by sicofante on 2007-12-24
> **Epilonsama said:**
> I tried this but when u type firefox-3.0 or click on the menu link, it says :
It worked for me. It didn't at first because the last command
```

sudo ln -s /usr/lib/firefox-3.0/firefox /usr/bin/firefox-3.0
```had failed.

You have to remove the original /usr/bin/firefox-3.0 and then execute the ln command.

In other words:

```
sudo rm /usr/bin/firefox-3.0
sudo ln -s /usr/lib/firefox-3.0/firefox /usr/bin/firefox-3.0
  
```I've also found why launching firefox from the downloaded tar won't work. The launching script will look for a firefox in the path and it'll always find the old firefox first. So the script in the beta files will work only if you don't have the stable Firefox 2 installed (or if you modify the script, which is out of the question for non-programmers).

---

### Post by fiskking on 2008-06-29
> **climber117 said:**
> Don't know what folder you're referring to, but here's how I did it. Grab the beta from [http://www.mozilla.com/en-US/firefox/all-beta.html]("http://www.mozilla.com/en-US/firefox/all-beta.html"). Download the file for Linux for your language. You'll download a tar archive. Extract it (right-click and hit "Extract here"). Doesn't matter where you extract it. Open a terminal and cd to the folder where you extracted it. Then: ```
sh firefox
``` That should run the beta version of Firefox. Do not close the terminal, or Firefox will close too. Firefox will probably disable all your extensions and themes, but when I went back to Firefox 2, it had automatically re-enabled them. Hope this helps.


files extracted to tmp folder, typed ¨sh firefox¨ to no avail.
also tried ¨sh firefox-3.0.  displays can´t open ..

---

### Post by fiskking on 2008-06-29
answered above I think

---

