---
title: "using mp3player with ubuntu?"
date: 2007-03-14
forum: Absolute Beginner Talk
---

### Post by rudedcam on 2007-03-14
cannot use my sansa e260 with ubuntu. why and how can I?


cannot install program given with mp3 player (see pic01)
error code (0x8000ffff) means
"when administrator tries to install sansa media converter on a windows 2003 server"

since i use linux and not windows... getting such error messages is not even making sense! 

with the MCS mode, ubuntu sees the mp3player as an external drive.
 Yes, can drag and drop files to the mp3player. but when i delete them, the files seems to disapear but the memory of the mp3player IS NOT cleared
ex: mp3player as 4G, put 1G of music in = 3G remaining. delete all the music but still 3G remaining and not 4G.

format the mp3player then?
the mp3player doesn't have such function. 

I called the company support line and they told me there was 2 ways to format:
1. connect by MTP mode with sansa media converter (sold with the mpsplayer) (the one i cannot install) 
2. connect by MCS mode and right click on the drive and use "format" to format the whole drive (on a Windows operating system)

that's when I told the dude on the support line that i used Ubuntu he replied something like " No, Don't, Cannot. 'cause you HAVE to use windows! we don't support linux " that was the end of the help! :lolflag: 

my question is.... how can i format the mp3player on MCS mode?
or
how can i install the program?

:popcorn:  thanks for helping!

---

### Post by airencracken on 2007-03-14
What programs have you tried using to work with it like an mp3 player. amarok for instace?

---

### Post by Belyel on 2007-03-14
> **rudedcam said:**
> cannot use my sansa e260 with ubuntu. why and how can I?


cannot install program given with mp3 player (see pic01)
error code (0x8000ffff) means
"when administrator tries to install sansa media converter on a windows 2003 server"

since i use linux and not windows... getting such error messages is not even making sense! 

with the MCS mode, ubuntu sees the mp3player as an external drive.
 Yes, can drag and drop files to the mp3player. but when i delete them, the files seems to disapear but the memory of the mp3player IS NOT cleared
ex: mp3player as 4G, put 1G of music in = 3G remaining. delete all the music but still 3G remaining and not 4G.

format the mp3player then?
the mp3player doesn't have such function. 

I called the company support line and they told me there was 2 ways to format:
1. connect by MTP mode with sansa media converter (sold with the mpsplayer) (the one i cannot install) 
2. connect by MCS mode and right click on the drive and use "format" to format the whole drive (on a Windows operating system)

that's when I told the dude on the support line that i used Ubuntu he replied something like " No, Don't, Cannot. 'cause you HAVE to use windows! we don't support linux " that was the end of the help! :lolflag: 

my question is.... how can i format the mp3player on MCS mode?
or
how can i install the program?

:popcorn:  thanks for helping!

So, I can tell you straight up that you won't get their program to install.  Ever.  It's a windows program and won't install directly onto Ubuntu.  You could try using wine (an application layer to let you run windows programs), but quite frankly, I think that it probably won't work, either.  Let's consider other options.  There are several programs in Ubuntu that can help manage an mp3 player.  The best program I've used is called amarok, and it syncs up well both with my ipod and my creative zen micro.  The ipod also shows up in Ubuntu as a disk drive.

I'm unfamiliar with the normal sync-ing process of that particular mp3 player.  If you normally just drag the files to the player, then that will work in Ubuntu.  However, to make sure the changes to the files on the player (recognized as a drive) are applied, you MUST eject the drive.  You eject it in ubuntu by right clicking on the icon for it (on the desktop) and selecting eject.  This will write the changes to the drive and you should see the updated storage space.  

Definitely search the synaptic package manager for amarok, and look around the forums for other folks who have that mp3 player.  If it's being recognized by ubuntu at all, your 97% of the way to having it working perfectly :).

---

### Post by Josey on 2007-03-14
I think that you you are moving them to trash instead of deleting.  In your file manager click on 'view' 'show hidden files'  delete items in trash on the external drive.

In the future use the delete key to delete off that drive.

---

### Post by noob_saioke45601 on 2007-03-14
do you have your .mp3 player set to msc instead of auto detect? i had the same issue with my sansa c140 .mp3 player. set it to msc mode then open up my computer, it will be listed there.

in order to switch to msc mode, open up the settings in your mp3 menu. next find text that says USB and select it. then select msc instead of auto detect.

when you move .mp3s to your mp3 payer dont unplug it immediately when your finished. you must right click on the driver in computer and select eject. wait a few secs then unplug your mp3 player and your files should be on it.

now about your question. format dont even show up when you right click on the drive so that i cannot answer sorry.

---

