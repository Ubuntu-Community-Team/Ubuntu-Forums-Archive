---
title: "Installing Stardict dictionaries"
date: 2006-07-17
forum: Absolute Beginner Talk
---

### Post by lennyjames on 2006-07-17
I am having a little trouble installing the dictionary files that I've downloaded for Stardict.

I used the command: 

**tar -xjvf stardict-oald-2.4.2.tar.bz2**

and that worked fine but when i used: 

**mv a /usr/share/stardict/dic**

to move the file over to the directory, I got this error:

**mv: cannot stat `a': No such file or directory**

So, I tried to manually move the files to the directory but the system won't allow me to do so. In addition, I cannot change the permission of the 'usr' forlder in order for me to copy over.

Any suggestions?

---

### Post by lennyjames on 2006-07-18
I'm still having trouble with this. Any ideas? Anyone?

---

### Post by Kurt` on 2006-07-18
Well, basically you're trying to move a file that doesn't exist. :)

# tar -xjvf stardict-oald-2.4.2.tar.bz2

should create a new folder called stardict-oald-2.4.2. Switch into that folder:

# cd stardict-oald-2.4.2

then type 'ls' and see if the "a" file you're looking for is in there.

Also, if the /usr/share/stardict/dict directory does not exist, you'll have to create it. (most likely via 'sudo mkdir')

Maybe you can post a link to the guide you were using? (or the Readme or whatever)

---

### Post by lennyjames on 2006-07-18
> **Kurt` said:**
> Well, basically you're trying to move a file that doesn't exist. :)

# tar -xjvf stardict-oald-2.4.2.tar.bz2

should create a new folder called stardict-oald-2.4.2. Switch into that folder:

# cd stardict-oald-2.4.2

then type 'ls' and see if the "a" file you're looking for is in there.

Also, if the /usr/share/stardict/dict directory does not exist, you'll have to create it. (most likely via 'sudo mkdir')

Maybe you can post a link to the guide you were using? (or the Readme or whatever)

Thanks Kurt, I feel a little embarrased. I discovered 'a' equated to the file I wanted to move! :p  Anyway, after the discovery, I did an 'ls' and got three file names, e.g., oald.dict.dz., etc.

Then I :

**mv oald.dict.dz /usr/share/stardict/dic**

And got:

**mv: cannot move `oald.dict.dz' to `/usr/share/stardict/dic/oald.dict.dz': Permission denied**

I can see the folder if I browse to the location but I have no permission to copy anything into it, even though I tried to do so manually. The folder 'usr', 'share', 'stardict', and 'dic' all have permission to write but I can't move anything into them.

I tried **sudo mkdir** but but:

**mkdir: cannot create directory `/usr/share/stardict/dic': File exists**
I'm stumped...:(

EDIT: I was using commands from this page:
[http://stardict.sourceforge.net/Dictionaries.php]("http://stardict.sourceforge.net/Dictionaries.php")

---

### Post by Kurt` on 2006-07-19
```
mv: cannot move `oald.dict.dz' to `/usr/share/stardict/dic/oald.dict.dz': Permission denied
```

That folder is owned by the root user, so you'll have to prefix the command with sudo. You can only write a file to folders you have write access to (but root can write a file anywhere).

# sudo mv oald.dict.dz /usr/share/stardict/dic

The mkdir command failing means that the directory already exists. That's fine.

Note: In case you don't know yet, I will explain. 'sudo' enables you to run a command as the root user, the *only* administrator user on the system. Root has the power to remove/change ANY file on the system. Be careful when running any commands prefixed with 'sudo', especially 'rm'.

---

### Post by lennyjames on 2006-07-20
Thanks Kurt`! That did the trick! 

I didn't understand the 'sudo' command before but now I know how powerful it can be! Now, stardict is running perfectly

---

### Post by patrick295767 on 2006-07-20
Hi, 

Additionally, would you know you can find some dictionaries in the repos? 

apt-cache search dict

Greetz

For example :
```
apt-get -f -y install stardict
apt-get -f -y install dict-freedict-spa-eng
apt-get -f -y install dict-freedict-fra-deu
apt-get -f -y install dict-freedict-fra-eng

apt-get -f -y install dict-freedict-fra-nld

apt-get -f -y install dict-freedict-slo-eng

apt-get -f -y install dict-freedict-eng-deu

apt-get -f -y install dict-freedict-eng-fra

apt-get -f -y install dict-freedict-eng-nld

apt-get -f -y install dict-freedict-eng-spa
apt-get -f -y install dict-freedict-eng-rus

apt-get -f -y install dict-freedict-nld-eng
apt-get -f -y install dict-freedict-nld-fra
apt-get -f -y install dict-freedict-deu-eng

apt-get -f -y install dict-freedict-deu-fra
apt-get -f -y install dict-freedict

apt-get -f -y install dict-gcide # A Comprehensive English Dictionary
apt-get -f -y install dict-moby-thesaurus # Largest and most comprehensive thesaurus
apt-get -f -y install dict-wn # Electronic lexical database of English language for dict
apt-get -f -y install dictd # Dictionary Server
```

---

### Post by Rickydd on 2008-01-05
> **Kurt` said:**
> Well, basically you're trying to move a file that doesn't exist. :)

# tar -xjvf stardict-oald-2.4.2.tar.bz2

should create a new folder called stardict-oald-2.4.2. Switch into that folder:

# cd stardict-oald-2.4.2

then type 'ls' and see if the "a" file you're looking for is in there.

Also, if the /usr/share/stardict/dict directory does not exist, you'll have to create it. (most likely via 'sudo mkdir')

Maybe you can post a link to the guide you were using? (or the Readme or whatever)

i get help in this answer . thank you very much

---

