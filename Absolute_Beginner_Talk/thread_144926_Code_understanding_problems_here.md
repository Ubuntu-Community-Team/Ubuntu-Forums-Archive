---
title: "Code understanding problems here"
date: 2006-03-15
forum: Absolute Beginner Talk
---

### Post by m00nd0g on 2006-03-15
Hi ... Someone want to explian to me the repositories with me here , If I have everything check off ? Doesn't that mean that everything is set to enable ? Thanks

---

### Post by chimera on 2006-03-15
the list of repositories is in /etc/apt/sources.list

you can access and edit it by entering

```

sudo gedit /etc/apt/sources.list

```

in terminal (which is located in the applications->accesories menu). You will then be prompted for your password (the one you entered during installation). Enter it and press enter. Now, a text editor should show up with the list of repositories. All the repositories with a # in front of them are not used. In order to make them usable, remove the # in front of them. Now, click the 'file' menu and click 'save'. Close the text editor, and in terminal, type

```

sudo apt-get update

```
again, you will need to enter your password. Now, the new repositories you enabled will be used. The time this takes depends on the speed of your internet connection.

---

### Post by m00nd0g on 2006-03-15
Hi ... Thanks for the response , So let me see if I got this right ? If I was to perform from this link below and stop at just before  "Adding Outside" part ? Are you saying that I still need to do what you have suggested ? Or by doing from that link is that all  I need to do to have them all enable as well ? 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

TIA ...

---

### Post by Klaidas on 2006-03-15
You can decide if you want to use extra resposities or if you don't.
Like, backports: they might give you newer version of programs, but they are not tested by the security team. :)

---

### Post by meborc on 2006-03-15
[QUOTE=m00nd0g]Hi ... Thanks for the response , So let me see if I got this right ? If I was to perform from this link below and stop at just before  "Adding Outside" part ? Are you saying that I still need to do what you have suggested ? Or by doing from that link is that all  I need to do to have them all enable as well ? 

[https://wiki.ubuntu.com/AddingRepositoriesHowto](https://wiki.ubuntu.com/AddingRepositoriesHowto)

TIA ...[/QUOTE]
the way discribed here in this thread is the *manual* way of doing things (read: the best way) ... when doing it like suggested in the wiki is the easy way of doing things... both do the same things as synaptic is just a GUI for apt-get (you can't use both at the same time)...

so, you can chose which way to go... ;)

---

### Post by chimera on 2006-03-15
Also, the method described in the wiki is for the old version of Ubuntu, the 4.10 warty warthog, which means you'll be downloading 18 months old software if you enable that repository.

---

### Post by m00nd0g on 2006-03-15
[QUOTE=chimera]Also, the method described in the wiki is for the old version of Ubuntu, the 4.10 warty warthog, which means you'll be downloading 18 months old software if you enable that repository.[/QUOTE]

Hi ... yeah I notice its not the exact same but its pretty well close though , Any ways I did figure out which path was the correct way for 5.10 but the bottom line is ? it does the samething ? So with that being said , If I have everything in the repo check off , That would mean its set for enable , Correct ?

---

### Post by chimera on 2006-03-15
not sure, the only way to be 100% sure is to do it the way I described:mrgreen:

---

### Post by m00nd0g on 2006-03-15
[QUOTE=chimera]not sure, the only way to be 100% sure is to do it the way I described:mrgreen:[/QUOTE]
Okay fair enough then , Though I am curious what most user's have enable in there repositories ? Is it wise to leave them all enable ? Thanks

---

