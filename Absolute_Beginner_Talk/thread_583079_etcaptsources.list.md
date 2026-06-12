---
title: "/etc/apt/sources.list:"
date: 2007-10-20
forum: Absolute Beginner Talk
---

### Post by limac on 2007-10-20
what is it? how do I get to it since for installing awn they are saying "just add the appropriate lines to your /etc/apt/sources.list:". so how do I get to /etc/apt/sources.list? first of all what is it?

thnx in advance

---

### Post by liamwithers on 2007-10-20
Open a Terminal. Type ```
sudo gedit etc/apt/sources.list
``` enter your password and then copy and paste the files need for Avant Window Navigator to the bottom of that file. Same thing with me yesterday.

Tell me if anything doesn't work :)

---

### Post by NilsE on 2007-10-20
> **limac said:**
> what is it? how do I get to it since for installing awn they are saying "just add the appropriate lines to your /etc/apt/sources.list:". so how do I get to /etc/apt/sources.list? first of all what is it?

thnx in advance

It is the config file that lists all of the Ubuntu repositories where the software resides.

You can either "open with text editor" and add what you want or better yet use the tool in System/Administration/Software Sources.  Then check all the repos that are not checked or you can also follow the instructions to add repos that are not there already.

---

### Post by Paul820 on 2007-10-20
It's a list of all the places you get your software from, like updates and the programs you download through synaptic. It's just full of website urls.

---

### Post by Paqman on 2007-10-20
> **limac said:**
> first of all what is it?


It's the list of what repositories are enabled on your machine. Adding an entry to it will make all the packages in that repo available through Synaptic. You should only add repos that are from a source you trust.

You can also add repos to it in System > Adminstation > Software sources > 3rd Party if you don't like editing files manually.

---

