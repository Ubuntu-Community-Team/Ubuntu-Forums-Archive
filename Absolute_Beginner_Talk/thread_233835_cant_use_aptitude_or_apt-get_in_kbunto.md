---
title: "cant use aptitude or apt-get in kbunto"
date: 2006-08-10
forum: Absolute Beginner Talk
---

### Post by xpod on 2006-08-10
Could someone tell me if using the terminal in kbunto should be just the same as ubunto(i thought it was )

Ive just tried using the commands for updates and for getting synaptic and automatix but none seem to want to do anything as they should.

Have been using ubunto but have this on spare pc and have just tried for the first time to get it up to speed.

Kids are wanting me to put all games we get offered in add/remove on ubunto onto this too.

I thought synaptic would be the best bet.

---

### Post by nalmeth on 2006-08-10
what is the output of:
sudo aptitude update

---

### Post by davebgimp on 2006-08-10
Yeah, there should be no difference. Also, Kubuntu comes with Adept which is a GUI package manager, similar to Synaptic.

---

### Post by xpod on 2006-08-10
Okay i think i had a look at Adept but it looked a bit more complicated than synaptic but thats probably just me not having looked at it properly.

Now the update was okay too i think but ive had it just as long as ubunto but ubunto`s told me of about 200 updates so far and this NONE.

Is that right????

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done


Heres what i got trying to get synaptic

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo apt-get synaptic
Password:
E: Invalid operation synaptic
graham@spc1-lewi1-0-0-cust180dadskb:~$


If i can get what they want via that adept then that`ll do me.....i`ll just need to figure it out.......I was being lazy and trying to stick to what i thought i knew.............THOUGHT planted a feather and thought he`d grow a chicken eh

---

### Post by davebgimp on 2006-08-10
> **xpod said:**
> Okay i think i had a look at Adept but it looked a bit more complicated than synaptic but thats probably just me not having looked at it properly.

Now the update was okay too i think but ive had it just as long as ubunto but ubunto`s told me of about 200 updates so far and this NONE.

Is that right????

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done


Heres what i got trying to get synaptic

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo apt-get synaptic
Password:
E: Invalid operation synaptic
graham@spc1-lewi1-0-0-cust180dadskb:~$


If i can get what they want via that adept then that`ll do me.....i`ll just need to figure it out.......I was being lazy and trying to stick to what i thought i knew.............THOUGHT planted a feather and thought he`d grow a chicken eh

Use Adept. But to answer that problem, the correct method would have been:
**sudo apt-get install synaptic**

---

### Post by nalmeth on 2006-08-10
Oohh, ok, this is just a misunderstanding.

Synaptic is a frontend to apt-get. *It* uses *apt-get* to fetch and install all dependencies.

To use apt-get in the terminal, you would provide an argument like 'install' or 'remove'
EX.

sudo apt-get install synaptic
sudo apt-get remove synaptic

sudo aptitude install kubuntu-desktop
sudo aptitude remove kubuntu-desktop

kubuntu uses adept instead of synaptic I believe:

ALT-F2
kdesu adept

---

### Post by xpod on 2006-08-10
I knew it ..."problem user"....I knew it did`nt look right...lol
I sometimes wonder how i got this far....Cheers folks.....(duh!)

It dosent seem to have near as much as synaptic but i suppose that was the point of it being lighter eh

---

### Post by davebgimp on 2006-08-10
> **xpod said:**
> It dosent seem to have near as much as synaptic but i suppose that was the point of it being lighter eh

It just accesses the exact same repositories so everything is available as it would be with any other installation. Is that what you meant?

In earlier incarnations, I wasn't too hot on it, but with Dapper, Adept's gotten much better as a package manager. I'm no expert, but as far as my usage, for me it's on par with Synaptic.

---

### Post by nalmeth on 2006-08-10
No problem man, 

Do you mean not as many applications? There actually are, but in adept (:rolleyes:) you have to click the "unsupported" + "restricted" boxes, and click "all platforms".

I'm not a fan of adept... It has improved overtime, and will continue to, but I *never* use it.

---

### Post by xpod on 2006-08-10
but as far as synaptic is concerned.....

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo aptitude install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for synaptic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
graham@spc1-lewi1-0-0-cust180dadskb:~$



So is that something to do with already having a form of it??

I cant see any of the games in adept.....not yet anyway

---

### Post by davebgimp on 2006-08-10
> **xpod said:**
> but as far as synaptic is concerned.....

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo aptitude install synaptic
Password:
Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
No candidate version found for synaptic
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done
graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo apt-get install synaptic
Reading package lists... Done
Building dependency tree... Done
Package synaptic is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package synaptic has no installation candidate
graham@spc1-lewi1-0-0-cust180dadskb:~$



So is that something to do with already having a form of it??

I cant see any of the games in adept.....not yet anyway

The problem with the games is not with Adept or Synaptic for that matter. it would be with your sources.list and what repositories you use. Have you enabled the universe and multiverse repositories?

---

### Post by xpod on 2006-08-10
repositries i presume.......ANTHER new wonder?????????

---

### Post by xpod on 2006-08-10
sorry.......i knew what was coming there...

Im not sure how to do so...im looking at it and have clicked the rep`s tab but must be missing something......I`ll get there in the end eh

---

### Post by davebgimp on 2006-08-10
> **xpod said:**
> repositries i presume.......ANTHER new wonder?????????

Okay, I'm getting the picture here. Let's see...

Repositories contain software for all versions of Ubuntu. They all use the same repositories. You'll be needing to uncomment a few in your sources.list file. The link below will walk you through that. After you do it, type **sudo apt-get update** and reload Adept for more programs than you can handle! :p 

[http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories](http://ubuntuguide.org/wiki/Dapper#How_to_add_extra_repositories)

---

### Post by xpod on 2006-08-10
AAHHH now he realises........haha....thanks for that.

I already had the term "repositries"in the back of my head from all the reading ive done but it must have slunk further into that dark void of mine.. plus i aint really needed any more of them in ubunto this last week or so since i signed up for the ubunto thrill ride.

Between add/remove,synaptic and automatix theres more apps than i could ever use on that one...

I have to remember i chose THIS for this pc as it needed something a bit more streamlined to fit on it in the first place so it aint going to have ALL that stuff iis it..........IM ON IT....good man

---

### Post by xpod on 2006-08-10
sorry again but i used the two initial commands prior to copying the new list and got this

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
graham@spc1-lewi1-0-0-cust180dadskb:~$

Let me guess...Gedit.....wrong commands wrong sys!!lol

---

### Post by nalmeth on 2006-08-10
hehe, I'm sorry, it's not funny. Must be frustrating.

Try kwrite or kate as gedit is a processor for gnome, and you're in kde.

---

### Post by davebgimp on 2006-08-10
> **xpod said:**
> sorry again but i used the two initial commands prior to copying the new list and got this

graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo cp -p /etc/apt/sources.list /etc/apt/sources.list_backup
Password:
graham@spc1-lewi1-0-0-cust180dadskb:~$ sudo gedit /etc/apt/sources.list
sudo: gedit: command not found
graham@spc1-lewi1-0-0-cust180dadskb:~$

in the command, replace gedit with kate, Kubuntu's editor.

---

### Post by xpod on 2006-08-10
Ha Ha......for somebody who was still getting his DLL`s and his LOL`s mixed up for the last few months ive been using computers i do ok.....

....with a little help from my friends.....

it was short and sweet with windows but here i AM and here im staying!!!

My God... the list is endless ,it dosent even seem to move when i scroll down now....I should be able to shut them up with that lot eh..lol

---

### Post by xpod on 2006-08-11
Well...it should have been enought o shut them up.

If i choose to install something from the adept package manager should it then just appear in the menu`s..?

Since adding those repositries the add/remove app has also got a bit more in it than what it had and if i choose something from there it install`s and appears in the meuu`s quite alright.

The same is not seemingly the case with adept though.

Is there something more one needs to do with adept to USE the installed apps??....EVEN the help dosent seem to work just now.

Ive been used to the simplicity of automatix and add/remove but using these package managers seems like a different kettle o fish.

---

### Post by davebgimp on 2006-08-11
> **xpod said:**
> Well...it should have been enought o shut them up.

If i choose to install something from the adept package manager should it then just appear in the menu`s..?

Since adding those repositries the add/remove app has also got a bit more in it than what it had and if i choose something from there it install`s and appears in the meuu`s quite alright.

The same is not seemingly the case with adept though.

Is there something more one needs to do with adept to USE the installed apps??....EVEN the help dosent seem to work just now.

Ive been used to the simplicity of automatix and add/remove but using these package managers seems like a different kettle o fish.

Both Adept and Synaptic are just GUIs for Aptitude. They read from the exact same repositories, so you're not going to have one  with something and the other not, unless your repositories are changed. If you think you are missing some programs, you need to look at your sources.list. Compare it against the list from a PC that DOES have what you want, see what's missing and add it to the list.

As long as the URL is correct and uncommented, Adept will read it fine.

---

### Post by xpod on 2006-08-11
Hi ..im not sure if i said but kubunto and ubunto are on different pc`s

Im not using the the twwo desktops on one sys.I understand a litte more though ...i think the more i read at times the more i get confused..

I was just wanting to really know "where" the couple of things i installed with adept are....They dont show up like things i install with the add/remove function.

I was following somebody else with a similar prob just as i noticed the reply to this......They cant find the packages the used synaptic to install on Ubunto....I gathered any answer they got would also be my answer..

They were advised to get the debian menu WHICH i do have on the pc with ubunto but cant seem to find that either here(repo`s eh?_

HA HA....as you`ve already gathered eh...lol

---

### Post by davebgimp on 2006-08-11
I answered your question in another thread you posted. 

You can either ALT + F2 and type the program name or open a terminal and type the program name. If you're not sure you can type a few letters and TAB to either complete or be presented with programs whose names might fit.

Also when you log out and back in, Kubuntu's program menu will rebuild. An easier way is to just right-click the menu icon, click edit and then save without changing anything. The menu will rebuild and your programs should be listed.

I understand that you have more than one computer. I'm saying, look at the sources.list file on one and compare it to the other if your missing programs in Adept or Synaptic. One or the other probably has an extra repository the other doesn't.

---

### Post by xpod on 2006-08-11
I ve got you now mate....sorry for being so exasperating.

I had no intention of touching the kubunto untill i had mastered(?)the ubunto but ive got a bunch of kids fighting over the m.e they use so i thought i`d get this in a child ready state.

i did`nt intentionally ask you twice i had just been following somebody else with a similar problem....sorry

It`s easy enough getting confused trying to get one up and running but 2 is pushing the bounds feasability me thinks.

It`s all dawned on me now though so i should be ok for now.........

...Until i try something else that is..thanks a lot..good man

---

### Post by davebgimp on 2006-08-11
No problem.

Hey, if this pc's for the kids, you might be interested in Edubuntu

[http://www.edubuntu.org/](http://www.edubuntu.org/)

It's a variant of Ubuntu that's geared towards kids, education, etc. It also uses Gnome. I have a few friends that resurrected old pcs with Edubuntu for their kids and they really like it.

---

### Post by xpod on 2006-08-11
Well thanks..i had noticed it on my travels.

believe it or not ive got a 13yr old boy and he aint intrested in pc`s other than going on graffiti creator to "create"....mmmm

the rest are all young girls who love writing their storys and to a degree actually trying to use the thing.

They`ll all want their OWN eventually and that was the sole reason i sat down at that m.e a few months back.....then scooted through an XP and here i am!!!

Well one of the apps i got was the 3dchess but when i try run it (alt+f2)
it just tells me it "could not run specified command".

I also tried it in the konsole to no avail.....???????????

Let me guess.....wrong sys??????

---

### Post by nalmeth on 2006-08-11
For whatever reason, sometimes games aren't added properly to menus. The binaries are all in /usr/games.
cd /usr/games
ls
./3dchess (if that is the name, you put the period and the slash in front to execute it).

A neat little app you may like is xfce4-appfinder. It may still not show all the games, but it seems to find most everything. Debian Menu is a good call too, it should show up in the Kmenu. You may have to restart KDE for it to show.

---

### Post by xpod on 2006-08-11
Hi...i was`nt sure if i could mabey only get stuff with the "K" for kde,i tried the 3d desktop it has too but could`nt find that either

Does ANY package that is in there then work on any system...Ub & Ku?

I was`nt sure if that was the one everybody is going on about which i would`nt be able to use anyway.

So i need to put certain prfix`s in front for some apps.

Some of the other stuff(with a K)i got appeared in the menu but some dosent.

ive got the debian on the ubunto,but on the Kubutno i can see it if i right click the kde and look at the menu editor but it dosent show in the menu proper..I had saved the menu

---

