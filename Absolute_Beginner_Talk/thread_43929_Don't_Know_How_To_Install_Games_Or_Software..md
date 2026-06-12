---
title: "Don't Know How To Install Games Or Software."
date: 2005-06-23
forum: Absolute Beginner Talk
---

### Post by John4486 on 2005-06-23
Hi,

Today I Installed Ubuntu Linux And I Got exploring it immediately. i learned how to make backgrounds and i'm playing mp3's too (finally). my problem is that i downloaded some freeware games and i just extract them from the (.tar.gz) archive and then i'm stuck....don't know what to do. i also checked the readme and still don't know. help me pls. thanks in advance.     (I Am Using A Linux Operating System For The 1st Time In My Life).

---

### Post by Kvark on 2005-06-23
Use the Synaptic Package Manager (under "System -> Administration" in the menues on top) if at all possible. Just put checkboxes for the programs you want to install and click apply. Very easy.

To download from a website and install manually is more work, and it's easy to mess up. So do that only when you can't find the program (or another program that fills the same function) with the search function in synaptic.

Check out these two links:

[http://www.ubuntulinux.org/ubuntu/components/document_view](http://www.ubuntulinux.org/ubuntu/components/document_view)

[http://ubuntuguide.org/#extrarepositories](http://ubuntuguide.org/#extrarepositories)

---

### Post by poofyhairguy on 2005-06-23
[QUOTE=John4486] (I Am Using A Linux Operating System For The 1st Time In My Life).[/QUOTE]

Well then let me first say welcome.

And then let me say- this is one area where windows is way different from Linux.

You can't just download software from the website of the maker and run it like in Windows (well...you can....but its hard).

In Ubuntu, you download all the software from Ubuntu. All of the best software is packaged to work on Ubuntu. TO get it?

Go to "system" "administration" then "synaptic package manager"

Thats the goldern ticket. Hit refresh. Then search for whatever you want!

---

### Post by Lunde on 2005-06-23
[QUOTE=John4486]Hi,

Today I Installed Ubuntu Linux And I Got exploring it immediately. i learned how to make backgrounds and i'm playing mp3's too (finally). my problem is that i downloaded some freeware games and i just extract them from the (.tar.gz) archive and then i'm stuck....don't know what to do. i also checked the readme and still don't know. help me pls. thanks in advance.     (I Am Using A Linux Operating System For The 1st Time In My Life).[/QUOTE]

**A good place to start is..**

Lots of apps and stuff here:
[www.ubuntuguide.org](www.ubuntuguide.org)

And more here
[http://ubuntuforums.org/showthread.php?t=31094](http://ubuntuforums.org/showthread.php?t=31094)

mostly **tar.gz** and **tar.bz** has a guide of how to install it. Best to start with a few **apt-get install** before you go on to the tar.gz installations.

But for **tar.gz** the command to unpack the compressed file is:

$ tar zxvf

And **tar.bz:**

$ tar -Ixvf 

Place the file in a folder in your /home/username, then open a terminal and move to that folder. then run the above command to extract the file (Do not include the $ in the command) 
Then mostly there is a new folder in the extracted tar file and inside that folder there are most likely a guide / readme file

---

### Post by weasel fierce on 2005-06-24
I hate to ask the really dumb question, but... how do I switch to a specific folder, using the terminal ?

---

### Post by poofyhairguy on 2005-06-24
[QUOTE=weasel fierce]I hate to ask the really dumb question, but... how do I switch to a specific folder, using the terminal ?[/QUOTE]

its not dumb

$cd /folder you want

---

### Post by John4486 on 2005-06-24
Hi,

Thanks For All Your Help Guys. You Helped Me Alot   :-P

---

### Post by weasel fierce on 2005-06-26
ah.. so sort of like old DOS :)

Very helpfull. Thanks!

---

