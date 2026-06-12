---
title: "Noob Needs Media"
date: 2007-04-13
forum: Absolute Beginner Talk
---

### Post by linuxnoobie on 2007-04-13
Hello People,

 I'm giving linux a second shot. Nothing was wrong with it. I've just been brainwashed by Corporate America and can't seem to break the habit. There are some issues that I have come by. I hope you guys have answers to them. (I'm using Kubuntu also if you guys need that to answer these questions)

My main problem is Media, Media, Media. I need my MP3's and I need my Flash. Is there an easy way to get an mp3 player (such as sudo apt--get)? I don't really understand the whole downloading and installing thing with linux. If someone could explain that or provide a link that would be great.

Onto Flash. I went to youtube and couldn't watch any videos because I needed the flash player. I clicked their link, went to adobe, and downloaded the tar.gz file (tarball, I believe is what they're called). Then following their instructions, it seemed as though I was doing stuff right, until when it went to install, it said it didn't support my dual processors or something like that. Is there a way a can get an older plugin or maybe a plugin by someone else. Step by Step instructions couldn't hurt either :)

I was also reading the tutorial on extra repositories (because I don't really know how else to get programs) Their instructions are as follows:

1. Start by choosing K-Menu-->System-->Adept (Package Manager) from the desktop menu system.

2. Select View-->Manage Repositories is the Adept menu

3  .To enable the universe repository, find the line with the universe component, right click the line, and click enable.  <-------Right there is where i have the problem. The only line I see with universe in it reads like this:
comment##universe Will Not recieve any review or updates from ubuntu security.  
To tell you the truth, I don't even know if I'm looking in the right place.  I hope at least some of my questions can get answered. And if you guys have any questions for me I am going to be aft till about 10:30 EST then I will answer all your questions.

---

### Post by richbarna on 2007-04-13
You will find everything you need on one page... [The Ubuntu Document Storage Facility]("http://doc.gwos.org/index.php/EdgyCust")

Another way to edit your sources list is to do it manually from the Konsole with Kate text editor, like this:-
Open your Konsole (Terminal) and type:
> kdesu kate /etc/apt/sources.lst 

You will see the sources list, with each line beginning with a comment (**#**) before them
like this:-
> **[FONT=monospace]#[/FONT]**deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 

Remove the comment so it looks like this:-
> deb [http://kubuntu.org/packages/kde-latest](http://kubuntu.org/packages/kde-latest) edgy main 

Then you can save the file and close Kate.

Now in the terminal you just need to do an:-
> sudo apt-get update

And you can access all the software you need from the repositories.

Good Luck ;)

I also have a link to the 100 best Ubuntu guides, Official and user's sites and bloggs
|
|
|
v

---

### Post by Maestro23 on 2007-04-13
These should help:


Installing Software:
[http://cutlersoftware.com/ubuntuinstall/](http://cutlersoftware.com/ubuntuinstall/)
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware) (lots of other good stuff)


Managing Repositories: [https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto](https://help.ubuntu.com/community/Repositories?action=show&redirect=AddingRepositoriesHowto)


Restricted Formats(mp3, playing DVD, etc..): [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

### Post by linuxnoobie on 2007-04-13
Thanks everyone. I'm sure I'll find my answers in here. Just looks like I got a lot of reading to do.

Hopefully, in a couple of weeks, I can remove my dual boot.

-Noobie

---

