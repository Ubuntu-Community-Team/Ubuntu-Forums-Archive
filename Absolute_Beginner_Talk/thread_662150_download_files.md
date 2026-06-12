---
title: "download files"
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by whiteguy on 2008-01-08
how do this stuff 

how do i download wine?

and is there a program called barrel or somthing like that that allows you to have like a 3d desktop?

can i get nero on ubuntu?

does ubuntu automatically detect my graphics card?

where is my trash bin located? how do i empty my trash bin in my terminal?

how do i get my computer to play mpeg, wmv, avi, iso, and other video formates when im online?

i have ubuntu 7.10
i also have the nvidia gf 7600 7series but i dont know the driver i have

---

### Post by Pevichaey5 on 2008-01-08
System>>Administration>>Synaptic Package Manager

use the search facilities in here to install just about anything, nero Linux i don't find very good, i prefer poweriso

---

### Post by lamalex on 2008-01-08
Wine:
[LIST]
[*]Go to: System > Administration > Synaptic Package Manager
[*]Search for wine
[*]Click to select "wine", then click apply.
[/LIST]

You are thinking of beryl. Beryl is dead, compiz-fusion is a merger between Compiz and Beryl. It is included and enabled by default in Ubuntu 7.10. To turn it on, if supported,[LIST]
[*]Go to: System > Preferences > Appearance > Visual Effects
[*]Select your desired level of effects
[*]OPTIONALLY:
[INDENT][*]Install Compiz Advanced configuration editor
[*]install compizconfig-settings-manager with Synaptic[/indent]
[/LIST]

No, there is no nero for Ubuntu however you might like gnomebaker or k3b

Yes Ubuntu automatically detects your graphics card, however it might require special drivers for advanced features such as 3D if it's an nvidia or ati card.
To install these drivers: [LIST]
[*]Go to: System > Administration > Restricted Drivers Manager
[*]Click to install the ATI or nVidia driver
[INDENT] ! For ATI cards, you must also install xserver-xgl from Synaptic[/INDENT]
[/LIST]

Your trash bin can be found in the bottom right hand corner on your lower panel. In terminal you would [code]rm -rf ~/.Trash/*

When you try and play the media, Ubuntu should prompt you to install the codecs

---

### Post by Sef on 2008-01-08
> how do i download wine?

Applications > Add/Remove > change top right bar to All Available Applications > search: WINE > Click on box > click apply > click apply > close

> and is there a program called barrel or somthing like that that allows you to have like a 3d desktop?

It's called Compiz-Fusion.  But what graphics card do you have?  Not all work with C-F.  

First, System > Administration > Restricted Drivers Management

Second, System > Administration > Synaptic Package Manager

> can i get nero on ubuntu?

Yes, [Nero]("http://www.nero.com/ena/linux3.html") on Ubuntu.

> does ubuntu automatically detect my graphics card?

It most likely will detect without any problems.  

> where is my trash bin located? how do i empty my trash bin in my terminal?

In the task bar on the bottom right.

> how do i get my computer to play mpeg, wmv, avi, iso, and other video formates when im online?

Read [Restricted Formats]("https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs").  Note: Most of the time, if you try to play a disk, it will ask you if you want to install the codecs.

---

### Post by benrboone on 2008-01-08
how do i download wine? 
system > Administration > Synaptic package manger then do search for wine

and is there a program called barrel it was called beryl but in gusty 7.10 it has been changed to compiz fusion (it is already loaded 
go System > Preferences > Appearance then click on the Visual effects tab.  then choose your level.  Note more advance features are available do a search on compiz to get more info

there are nero like program available in ubuntu KB3 and such

to play video that you listed click on the video and it will ask you to install the necessary codecs.

For flash you will need to install flash player from adobe since the auto install has broken
here is more info it really quite easy
[http://ubuntuforums.org/showthread.php?t=636397](http://ubuntuforums.org/showthread.php?t=636397)

---

### Post by Sef on 2008-01-08
> No, there is no nero for Ubuntu



Not true.  I would suggest next time search for it instead of just posting something that is incorrect.   [Nero on Linux]("http://www.nero.com/ena/linux3.html")

---

### Post by benrboone on 2008-01-08
I did not say there was no nero in linux I just said there were similar programs to nero

quote
"there are nero like program available in ubuntu KB3 and such" 

I was not saying nero does or doesn't exist only that KB3 and gnomebaker and such are also available  note it does not say nero is not available

---

### Post by whiteguy on 2008-01-08
i go to system-admin-synaptic package manager and serch wine but the search doesn't show a thing about it

---

### Post by benrboone on 2008-01-08
I believe that you need to enable more repositories
this can be accomplished by system > Administration > Synaptic package manger
then click on settings repositories.  I have enabled the proprietary drivers 
and the restricted as well as the third party software ones on the next tab
when i do a search wine shows up
I don't personally use wine so I don't know much more than this

---

### Post by whiteguy on 2008-01-08
so system-admin-synaptic-settings-reposit-
than what do i do so that i can find wine

---

### Post by Sef on 2008-01-08
> did not say there was no nero in linux I just said there were similar programs to nero

quote
"there are nero like program available in ubuntu KB3 and such"


That is correct and I adjusted my post.  Thank you for politely pointing out my error.

---

### Post by RomeReactor on 2008-01-08
> **whiteguy said:**
> so system-admin-synaptic-settings-reposit-
than what do i do so that i can find wine

Check all the boxes in the first tab ('Ubuntu Software') except for 'Source' and 'CD-ROM'. Close that window and, still in Synaptic, press the blue 'Reload' button. Then search for "wine" (make sure the "Look In" drop down menu is set to "Name").

As has been pointed out, Nero has a Linux version, but if you want a comparable level of features then I would recommend K3B instead.; if you only want to burn audio or data CDs, or data DVDs, then Nautilus (Ubuntu's file manager) already has that functionality built in, so there would be no need to install anything. Just insert a blank CD or DVD and you'll be asked whether to burn an audio or data cd, to burn a data DVD, or to make a copy.

---

### Post by benrboone on 2008-01-09
Then redo the search for wine
it will then show up
check the box for wine and apply

ops didn't look at page two sorry about the duplicate post

---

### Post by kleo skywalker on 2008-01-09
To enable all repositories, go to System-->Administration-->Software Sources.  Check all boxes except "Source Code" (I'm assuming you don't need this, but you can enable it if you need it.)
In Synaptic, install the **ubuntu-restricted-extras** package, that should take care of most of the file formats you want to play. For more information on these, see [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

---

