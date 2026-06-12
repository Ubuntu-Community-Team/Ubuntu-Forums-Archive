---
title: "abi word questions in dapper"
date: 2007-07-23
forum: Absolute Beginner Talk
---

### Post by orwellus on 2007-07-23
Hello:

I am currently using Dapper Ubuntu, and have a couple of questions about Abiword.

First, is there a way to customize the tool bar at the top (to add buttons), or change the icon theme? 

Second, does anyone know if there is a fix for the grammar checker? This is what's really bugging me. I've looked on the internet and on the Ubuntu forum,  and the only thing I can find is that there has been a problem with the Grammar checker for like two years. Yes, I do know about Language Tools for Open Office, and use it, but it doesn't put a green line under anything as you type the document. I like Abiword a little better, anyway, since it starts right up, and is a lot easier to use  than Open Office.

Any help would be appreciated.

---

### Post by pyros on 2007-07-23
> **orwellus said:**
> Hello:

I am currently using Dapper Ubuntu, and have a couple of questions about Abiword.

First, is there a way to customize the tool bar at the top (to add buttons), or change the icon theme? 

Second, does anyone know if there is a fix for the grammar checker? This is what's really bugging me. I've looked on the internet and on the Ubuntu forum,  and the only thing I can find is that there has been a problem with the Grammar checker for like two years. Yes, I do know about Language Tools for Open Office, and use it, but it doesn't put a green line under anything as you type the document. I like Abiword a little better, anyway, since it starts right up, and is a lot easier to use  than Open Office.

Any help would be appreciated.

The icons should change with your overal icon theme. while it should be possible to rearange the toolbars by going to View>Toolbars and unchecking lock toolbars, I can't get it to work. The grammar checking does not work in the ubuntu (or debian) version of abiword. Grammar checking may work in dapper, as it seems to have liblink-grammar4-dev. There is a bug filed against this, but I haven't seen any work on it in some time.
edit:
On second thought, it is there... It might be possible to recompile the source debs... with liblink-grammar4-dev installed...

---

### Post by orwellus on 2007-07-23
Thank you for your reply. Well that's too bad about the grammar checker. I will try to add that lib grammar and see if that works, but if it doesn't oh well.

---

### Post by pyros on 2007-07-24
> **orwellus said:**
> Thank you for your reply. Well that's too bad about the grammar checker. I will try to add that lib grammar and see if that works, but if it doesn't oh well.

I don't thing that it will work. do you have the abiword-plugins package insatlled?

---

### Post by orwellus on 2007-07-24
What I did was go into synaptic package manager and did a search for link grammar, and installed what came up. Next I downloaded the latest abiword and installed that. Then I went into synaptic package manager and installed the abiword plugin-ins. Then I started Abiword. In Abiword I checked what plugins were installed by going into Tools>Plugins (i think) and Abigrammar Check was listed among the plugins. BUT!!! As soon as I typed in something in Abiword it crashed. And kept crashing, every time I tried to used it. So I uninstall Abiword because it looks like it is all messed up now. Oh well, it was worth a shot. I'll probably have to reinstall Dapper to get Abiword back now.  I guess Ubuntu really does not like that Grammar Checker.

---

