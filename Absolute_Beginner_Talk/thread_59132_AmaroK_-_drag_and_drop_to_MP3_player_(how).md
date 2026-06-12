---
title: "AmaroK - drag and drop to MP3 player (how?)"
date: 2005-08-22
forum: Absolute Beginner Talk
---

### Post by aysiu on 2005-08-22
So, after trying out various music players (XMMS, Beep, Juk, Rhythmbox), I've sort of settled on AmaroK. 

The only thing that bothers me about it is that I can't seem to drag and drop songs to my non-iPod MP3 player. When I click on the device icon, it says I queue up songs to transfer to my iPod. I thought, "Hey, maybe they just *say* iPod, but it can be any MP3 player." So I tried it out. No go. 

Then, I tried dragging and dropping songs directly from AmaroK to my MP3 player's folder. It *seemed* to work, but what it really did was **move** the song to my MP3 player, not **copy** the song to my MP3 player. I don't want to move the songs--I want to copy them. 

This worked in Rhythmbox (which I ditched for other reasons, which I won't go into here). How do I enable this drag-n-drop capability for AmaroK? I didn't see any option for this in "Configure AmaroK." Any help would be greatly appreciated.

---

### Post by Jussi Kukkonen on 2005-08-23
[QUOTE=aysiu]The only thing that bothers me about it is that I can't seem to drag and drop songs to my non-iPod MP3 player. When I click on the device icon, it says I queue up songs to transfer to my iPod. I thought, "Hey, maybe they just *say* iPod, but it can be any MP3 player." So I tried it out. No go. 

Then, I tried dragging and dropping songs directly from AmaroK to my MP3 player's folder. It *seemed* to work, but what it really did was **move** the song to my MP3 player, not **copy** the song to my MP3 player. I don't want to move the songs--I want to copy them.[/QUOTE]
 I find it hard to believe that drag'n'dropping songs from the **Collection** tab would move them (instead of copying). Are you sure you weren't dragging from **Files** tab?

---

### Post by aysiu on 2005-08-23
[QUOTE=Jussi Kukkonen]I find it hard to believe that drag'n'dropping songs from the **Collection** tab would move them (instead of copying). Are you sure you weren't dragging from **Files** tab?[/QUOTE] Yes, I'm dragging the actual song from the playlist/library to the desktop/MP3 player, and it's actually moving the song, not copying it. I found it strange, too, because this didn't happen in Rhythmbox. Are you just finding it hard to believe, or have you actually used AmaroK and not found this to be the case?

---

### Post by Lord Illidan on 2005-08-23
I'm not sure, but can you rightclick on the songs and copy them? Or move them by middle clicking?

---

### Post by aysiu on 2005-08-23
[QUOTE=Lord Illidan]I'm not sure, but can you rightclick on the songs and copy them? Or move them by middle clicking?[/QUOTE] I tried that, too. When I right-click, nothing in the context menu comes up that's close to "copy." And middle-click and right-click dragging both just move the song. Do I have some kind of screwed up copy of AmaroK, or have other people experienced this, too?

By the way, I appreciate people trying to help.

---

### Post by Jussi Kukkonen on 2005-08-23
[QUOTE=aysiu]Yes, I'm dragging the actual song from the playlist/library to the desktop/MP3 player, and it's actually moving the song, not copying it. I found it strange, too, because this didn't happen in Rhythmbox. Are you just finding it hard to believe, or have you actually used AmaroK and not found this to be the case?[/QUOTE]

 :? When I wrote the last comment I hadn't tried it, now I have: I drag'n'dropped a song from both the collection-treeview and the playlist into Nautilus. The files were copied and the playlist item and the song in the collection stayed put... 

I am using version 1.3 (which is not the one packaged by Ubuntu), so there is a small possibility that this is a bug which was fixed between 1.2.3 and 1.3. **Could another Amarok user please test this?**

---

### Post by aysiu on 2005-08-23
[QUOTE=Jussi Kukkonen]:? When I wrote the last comment I hadn't tried it, now I have: I drag'n'dropped a song from both the collection-treeview and the playlist into Nautilus. The files were copied and the playlist item and the song in the collection stayed put... 

I am using version 1.3 (which is not the one packaged by Ubuntu), so there is a small possibility that this is a bug which was fixed between 1.2.3 and 1.3. **Could another Amarok user please test this?**[/QUOTE] That could be an explanation. I checked in Synaptic, and I have 1.2.4 installed. Do you think it could have something to do with my music files being stored on my Windows FAT32 partition (as opposed to in /home)?

---

### Post by seethru on 2005-08-24
[QUOTE=aysiu]That could be an explanation. I checked in Synaptic, and I have 1.2.4 installed. Do you think it could have something to do with my music files being stored on my Windows FAT32 partition (as opposed to in /home)?[/QUOTE]
 I have an ipod, and I can't even drag and drop my files into the queue window. Gives me a NO icon :/ I'm hoping this ins't because I'm using gnome w/ amarok.

---

### Post by aysiu on 2005-08-24
[QUOTE=seethru]I have an ipod, and I can't even drag and drop my files into the queue window. Gives me a NO icon :/ I'm hoping this ins't because I'm using gnome w/ amarok.[/QUOTE] I never even thought of that. I'll have to try it with KDE to see if I run into the same problem. And I did figure out that it's not my FAT32 partition. Even if my music files reside in /home/username/Desktop, I still get the same problem.

---

### Post by aysiu on 2005-09-12
Well, I'm finally using Kubuntu full-time, and I tried AmaroK in its native KDE, and guess what... the drag-n-drop worked! [Here it is in action](http://i22.photobucket.com/albums/b337/psychocats/amarok.png).

---

### Post by sophtpaw on 2005-09-12
[QUOTE=aysiu]Well, I'm finally using Kubuntu full-time, and I tried AmaroK in its native KDE, and guess what... the drag-n-drop worked! [Here it is in action](http://i22.photobucket.com/albums/b337/psychocats/amarok.png).[/QUOTE]


Well, looks like Amarok is not ready for my desktop. In my vain search for a music player i installed Amarok (1.2)from Synaptic went through the wizard and can't seem to play a thing.

Eventually crashed on, and that was that.
I use Gnome/Ubuntu

it doesn't have an icon. Went to configure Amarok/ Engine. all i have is aRts engine and maybe that is why i don't get sound?

Do i have to move to kubuntu to have a media player work?

Sorry, i don't mean to crash on your thread Aysiu, but since you got your to work now i thought you or someone here might be able to help

i appreciate it too,


--
sophtpaw

---

### Post by wildthing-zim on 2005-09-12
1st thing first , do you get sound when ubuntu loads ?? , if you dont your sound card needs help ...desperately 

if you have sound try playing a wav or midi file , if they work , you need mp3 support loaded , this is what i had to do , found it on the forum , search for play mp3's . that helped ..

---

### Post by sophtpaw on 2005-09-12
[QUOTE=wildthing-zim]1st thing first , do you get sound when ubuntu loads ?? , if you dont your sound card needs help ...desperately 

if you have sound try playing a wav or midi file , if they work , you need mp3 support loaded , this is what i had to do , found it on the forum , search for play mp3's . that helped ..[/QUOTE]

well i get sound. I can play cd's on my cd player. No i don't get sound when ubuntu loads because i followed a sound wiki for Alsa where i was told to disable that function, which had the overall effect of sounds working otherwise in Ubuntu where they werent' before. Like games etc


Xine plays my DVD's in dvd player
Xine does not play cd's in cdplayer? due to no mrl
cd player does play cd's!

Can someone help me fix xine: no mrl so it can also play cd's or at least can someone please tell me how to disable xine as my default cd player so i don't have to see the error message everytime,

thank you very very much,

--
sophtpaw

---

### Post by aysiu on 2005-10-30
I don't know if anyone has this problem, but I did find kind of a weird solution/workaround. I actually use JuK now (not AmaroK), but it's the same problem, and it's also the same solution.

Rather than dragging and dropping from AmaroK/JuK to some place in Nautilus, drag and drop the songs to some place in Konqueror (yes, Konqueror within Gnome), and it works.

---

### Post by patrickhmm on 2008-07-17
i did it in amarok!!!!
Okay i got this to work this way:

so drag your song from the playlist to a folder

BUT
BEFORE YOU LET GO OF THE MOUSE
>>>>HOLD DOWN CTRL KEY<<<<

you will see your cursor turns into a + sign

now let go. this should have copied the song not moved

this means it will copy not move

i hope that solves this issue :):):)

---

