---
title: "Another Linux/iTunes/iPod Post: My Thoughts"
date: 2007-06-26
forum: Absolute Beginner Talk
---

### Post by kasperbs on 2007-06-26
**I have now been using Linux and Ubuntu for quite some while and it has become clear to me what is missing from Linux that probably keep a lot of people away from switching totally. I have made the switch totally and is now exclusively working in Linux except from Photoshop running in a virtual machine, I will come back to that later.**

As I said I work exclusively in Linux I'm a webdesigner and I have no problems finding the apps I need to do my job. However I', also an iPod user and rely heavily on photoshop for my design work, and those two things has proven to be the hardest things to overcome in the switch to linux - and the single two things that takes up most of my time when I'm in front of a PC.

It didn't take me long to realize that there were no such thing as Photoshop for Linux - The GIMP is fine for hobbyist and some can actually do professional jobs with it. But it simply can't do all the things Photoshop can, and if you are relying on advanced techniques, The Gimp simply don't cut it. So I decided to run Photoshop in a virtual machine using VirtualBox which works very well - and I have a shared folder so that I can access my psd files from both linux and windows.

For my other problem: iPod and iTunes. I must admit there is a lot of great music apps in Linux but none of them  live of to the logic that iTunes follows in managing music and podcasts. I gues if you don't have an iPod you would be OK in Linux becuase you didnt have to sync files and you could just access you video podcast in a separate program. However if you own an iPod and want to use it to the full you have a problem in Linux, you can do everything in Linux but not as fast as you can in iTunes. I have tried nearly all the apps available for Linux regarding iPods and music management, but have come to the conclusion that it isn't possible to have an all in one app just like iTunes.

[SIZE="3"]**The logic of iTunes:**[/SIZE]
[SIZE="2"]Music Management:[/SIZE]
In iTunes you can manage your music in a logic way, when you import your music it is automatically copied to your library folder and organised in folders. If you decide to change the ID3 data of a song in iTunes it automatically updates the file name and folder structure in you library as well. - Thats the logic way of dealing with music, if you change your ID3 tag why wouldn't you want to change your filename as well to match that change, and your folder structure? - Banshee does a great job in importing songs and organising them - but if you decide to change a son within Banshee, lets say you change the artist name from ABBA to Beatles - it wont change your folder structure - That song will still be within the ABBA folder. Why?

If you change a name from your folder, it will automatically detect it in iTunes and give you a warning saying that the file has changed - iTunes is monitoring the folder for changes obviously. Banshee cannot do this. Some other apps can do so Rythmbox for example and amarok.

[SIZE="2"]Podcast Management:[/SIZE]
iTunes can subscribe to both video and audio podcasts logically - and sync them to the right folders on the iPod so that video podcasts show up under video podcast and not under audio podcasts. Floola does a good job with this - but Floola lives on the iPod and is not good for music management

iTunes can play both audio and video podcasts - songbird can do this but Songbird cant limit the number of podcasts that is being kept - meaning you have to manually deleting them after you have heard them or seen them. In iTunes you can tell iTunes to just keep the last two episodes of any podcast, I have yet to find an app that can do this. The closest I have come is that you can tell the app to delete podcasts after a certain amount of days. But what if you have podcasts that are updated everyday, or several times a day like news podcasts, and you have more in depth podcast like tutorials which are updated on a weekly or monthly bais. You would have to set it to a month to be sure that you will keep the tutorial until a new one is released, but this will also mean that you end up with hundreds of news podcasts that you dont really need.

Not to mention the iTunes Music Store - podcast library the possibilty to subscribe to tv-shows, games etc.

[B]To recap what I think is the main points that iTunes can do and what I would like to see in a linux app one day.
Logic relation between ID3 tags, filenames and folder structure.
Logic podcast subscription service - both for video and audio
Logic playback of both video and audio podcasts
The possibility of putting videos on your iPod[/B]

I haven't mentioned gtkpod here and for a good reason it doesn't let you subscribe to podcasts.

Some potentially useful apps if you want to try and make it up for iTunes is Floola which does a good job of subscribing and syncing podcasts, but doesn't work as a desktop multimedia player.

Songbird is great for that but bad when it comes to podcasting - But I think within a few years Songbird can be th eiTunes for linux That everyone is waiting for

banshee is a great app for music management but lacks the logic of the relationship between ID3 tags and filenames. Plus the podcasting feature is bad aswell and it only works for audio.

Please let me know how you think of this issue, and how you go about dealing with your music, video, podcast collection and syncing them to your iPod

---

### Post by eentonig on 2007-06-26
> **kasperbs said:**
> I have now been using Linux and Ubuntu for quite some while and it has become clear to me what is missing from Linux that probably keep a lot of people away from switching totally....

I disagree with this statement. Why does everybody who misses 'a' feature he was used to in windows, thinks that this is THE MISSING LINK for mass adoption?

For the rest. Allthough I can do all I want with my music library and iPod through amarok, I can understand your grieves. I don't share them. But I understand.

---

### Post by kasperbs on 2007-06-26
I like amarok as well and it is psobably the best all in one app at the moment and not everybody needs all the features of iTunes - and for audio amarok does a great job and does if you tweak a little also change the filenames if you edit the ID3 tags. It still can't manage your video syncing allthough you can as far as I know subscribe to video podcasts it has a hard time syncing them as video podcasts, and puts them in the audio podcasts folder on your ipod making them useless.

Could you please expand on what it is you disagree with?
> Why does everybody who misses 'a' feature he was used to in windows
I didn't say everybody, I'm a good example of that I miss iTunes but that doesn't keep me from switching. But i read a lot of posts here and there and have talked to a lot of people specially people that uses windows apps in their working life, that keep dual booting because of that one app. I even know of people just dual booting for Photoshop alone and other Adobe products. But it would actually be nice to hear how many people are dual booting because of one or two apps, I may be wrong and I actualy hope i am. I just personally know "A lot" that are dual booting just for Photoshop.

Just for curiosity do you have a video iPod? - I should probably have stated that my concerns are mainly regarding the video iPod version.

But thanks for your feedback

Edit: Just a quick question, Could you explain the easiest way to maintain a relationship between the ID3 tags and the file structure and file-names in Amarok, I have tried it but it seems a bit complicated and I'm probably doing something wrong. Thanks

---

### Post by coolen on 2007-06-26
To be honest, I'm far happier with my music in Ubuntu. Nothing I have in Windows comes close to the ease, simplicity, and aesthetic value of Rhythmbox, in my opinion. It's a perfect balance for me.
I hate the all-in-one approach. I like having these functions split up a bit. Particularly for syncing. My iPod has never touched iTunes, after seeing what a hastle it was for my brother. It took me half an hour to get the songs to the list, another twenty minutes trying to get it to sync, and after that, I still wasn't sure if it had worked.
In contrast, I open gtkpod, my song list is imported, and I can swap and choose at my leisure. Once I've reached a nice list, I let it go and make all the changes. It's simple, it's easy, and it's under my control.

In my experience, the iPod works fine under Linux. Far better than with Windows.
Of course, given the option, I'd go for something better than an iPod anyway...

---

### Post by kasperbs on 2007-06-26
Hi Coolen, thanks for your input.
I have been using Rythmbox As well and it is a nice app for music, but how do you go about organising your music in rythmbox. If your for example import a song an you decide to edit the ID3 tag on it to make it show up under Beatless songs for example, how do you then organize your folder to mimic that change. And how do you subscribe to video podcasts?

---

### Post by kasperbs on 2007-07-02
Well thanks for all your inputs, and if anyone is still interested in the debate I have managed to find a solution that works well under Ubuntu.

[SIZE="2"]**The 3 programs you need is amarok, gtkpod + iTunes+VirtualBox+WindowsXP**[/SIZE]
First of all I need iTunes to take care for Podcasts, especially Video Podcasts and transferring them to the iPod and put them in the right directory (i.e video podcasts ion the video folder and not audio)

Installl VirtualBox and then run WinXP inside it and use that to install iTunes. VirtualBox can be installed via Automatix, and if you got a WindowsXP key i recommend downloading the [rev06 windowsXP]("http://avaxhome.org/software/Windows_TinyXP_Rev06-eXPerience.html") version as it only takes up around 50mb ram, and all the bullshit windows programs are cut out.
The install the most recent version of iTunes and plug in your ipod and wait for windows to install the driver software. Now run iTunes and put a check mark in the manage music and videos manually, and in the sync only checked items. Then go to the podcasts tabs in the ipod browser window and choose the podcasts you want to sync and then sync your ipod. This will sync all your podcasts to your iPod. Well done.

Now it's time to get your music library synced to your iPod with a software that is capable of managing your music collection and organizing it in folders etc. Amarok can do that and it can also sync your library heres what you do.
Have amarok recognizing your iPod and then go to playlist and select smart playlists and then right click on the all collection playlist and choose sync to media device. This will sync that playlist to your ipod, and next time you connect your ipod, repeat this step and the all collection playlist will automatically be updated on your iPod. You can of course also sync other playlists.

Ok now you want to get your converted dvd movies on your ipod. Open gtkpod and load your ipod. Now add file or directory with your MP4 video files and click save. This will transfer the videos to the movies folder on your ipod and you can play them just as if you had transferred them with iTunes.

Hope someone can use this at least until we get a proper iPod software for Ubuntu that is capable of organizing our music on our harddrives writing proper id3 tags including writing album covers in the id3 which amarok can't do, but some software like easytag can do it. I believe that sunbird in a couple of years may go in this direction, but until then you will have to run windows if you want to get the most out of your ipod and ensuring that everything is synced perfectly.

For those that are not interested in video podcasts or interested in neatly organized audio podcasts you dont need itunes. Podcasts and video podcasts can be downloaded and synced to your ipod with other software but you will loose the folder structure on your ipod and you podcasts names will be something like > 010207_moyles-1404-carrie_getmarried-3804982.mp4
instead of 
> Moyles: Carrie Is Getting Married 22 June 07
in some cases you will also loose the folder structure on you ipod so that maybe your Moyles podcasts will show up in your ricky gervais podcasts directory and stuff like that.

---

### Post by kasperbs on 2007-07-02
> Of course, given the option, I'd go for something better than an iPod anyway...
Hi Coolen I have thought the same thing but I can't really find anything that can do the stuff that the Ipod can. What other players do you know that can do pocasts video and audio, play movies with tv-out and have 30+gb space, and can play other than only MP4 movie files?

I also hate that the ipod can only play those MP4 videos, it does it well though. Before I got my iPod I went through a lot of hassle with pocketPC's and stuff but they struggled to play the MP4 podcasts, and the battery life was bad too. But just like you I would like something better than an iPod, at the moment i bought mine though I just couldnt find anything better, so if you know of any that would be great

---

### Post by moore.bryan on 2007-07-02
[I]the solution is [rockbox]("http://www.rockbox.org/").
;-)
[/I]

---

### Post by moredhel on 2007-07-02
^ I was gonna say that :P

Using it right now, and it certainly has more games than the ones you have normally, and they are free! :D

---

### Post by moore.bryan on 2007-07-02
:popcorn:

---

### Post by cprofitt on 2007-07-02
Apple is the new evil empire.

iTunes is currently outlawed in some eurpean countries because of restrictive trade practices... and the iPhone actually requires iTunes to activate.

Apple = Darth Vader in his prime

Microsoft = Jabba the hut

---

### Post by rfurman24 on 2007-07-02
I do feel that everyone is entitled to their opinion but I do have to say I hate Itunes I did use it before I was able to get Gtkpod working. It is very illogical in its file structure if you ask me. I do not want my software telling me where or how to save my files. Gtkpod is very easy and straight forward. I load my Ipod add/change/remove files then save. It is very simple. As far as photoshop it does run with crossover office unless you use the cs3.

---

### Post by kasperbs on 2007-07-03
RockBox? I would love to have that installed instead of apples software if it fits my needs. But could you clarify a few things for me?
Can Rockbox Play back videos?
What software does it use to sync video podcasts?
and is the filenames on the podcasts something you can understand

> It is very illogical in its file structure if you ask me. I do not want my software telling me where or how to save my files
I understand that you want to save your files yourself but iTunes won't save your files for you unless you explicitly tells it to do it.

I just think its logical that when you for example import a cd that it automatically copies it to your library and organises it in Artist/Album folders.

I just want to state that I'm not writing here to do any kind of propaganda towards itunes or apple or anything. I would be the first to ditch iTunes if I found something that could replace it and do what i want it to do.

All I know is that I'm not the only Linux user that misses iTunes, and more power to you guys that hate iTunes, I do too, I just can't find a better replacement right now :(

I know the portable version of Photoshop runs in Crossover office, but if you use it professionally you need a stable installation, plus I can't install plugins in crossover office. But thanks for pointing it out

---

### Post by Raineer on 2007-07-03
Rockbox can do whatever you want with it.

Rockbox plays videos, and without being in the "Apple format", even on 'non-video' ipods like the Nano.  It can play ANY format audio.  You can sync whatever you need using ANY file management software, like **rsync**. Rockbox is something that works only on the iPod unit, so you get to decide how you manage files on the host (your PC). It doesn't necessarily "manage" anything, but it lets you do it all the way you like...which I prefer heavily. It also doesn't disturb the Apple firmware, in case you want to switch back and forth for some reason. 

Basically all I do is just manage my music collection with Amarok, and rysnc it to my iPod.  If I need to add/remove specific files it's as easy as going to Nautilius to manage my collection fast.

Going to Rockbox form iTunes is like going from Windows to Linux, once you understand what it can do you would NEVER think about going back, period.

---

### Post by kasperbs on 2007-07-03
That sounds interesting, I'm definitely going to try that out. Does that mean I can play DivX and AVI videos on my ipod? What program do you use to subscribe to video podcasts then?

I was suspicious because this list does not seem to support video files:

[http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-buildap1.html#x13-227000A]("http://download.rockbox.org/manual/rockbox-ipodvideo/rockbox-buildap1.html#x13-227000A")

---

### Post by Raineer on 2007-07-03
They need to be .mpg of near-close resolution, and they play through a "mpegplayer" plugin, but they are much easier to encode (read faster) than using iTunes to make a file "iPod ready" which when I used Windows took a VERY long time per file.  

As for video podcast subscription, I don't use them (I just manage my own), but I did a Google for Linux Video Podcasts in Google and found about 10 programs that said they do it in some fashion...so you'd be free to use any of these.

It's a paradigm shift in a player, and it will initially have a learning curve (probably not as bad as Linux :D ), but that's what the rockbox forums, wiki, and #IRC channel are all about. I'm active over there too and the users are quite helpful.

---

### Post by kasperbs on 2007-07-03
> As for video podcast subscription, I don't use them (I just manage my own), but I did a Google for Linux Video Podcasts in Google and found about 10 programs that said they do it in some fashion...so you'd be free to use any of these.
Yeah I have tried most of them, but they make file names unreadable. like I mentioned earlier in this post, and they are not good as managing them.

What about tv-out?

well if its only mpg, then I would have to encode them anyway, because all my movie files are divX or AVI

---

### Post by Raineer on 2007-07-03
Tv-out isn't supported on the Video 5G because they are still learning the hardware for it (but anyone is welcome to write it anytime), and that's the only reason I still use the dual-boot feature.  Yeah I noticed you mentioned the filenames earlier but since I just d/l my own and rename them. You must watch a lot more video podcasts than I'd have time for in a day :)

The Archos and Gigabeat are the main players the project started for, and then it was migrated to the iPod, which means the iPods don't have 100% of the features yet. The list grows all the time though.  Are the Divx and AVI files you have already around 320x200? If not you'd be re-encoding them anyway.

---

### Post by moore.bryan on 2007-07-03
> **kasperbs said:**
> All I know is that I'm not the only Linux user that misses iTunes, and more power to you guys that hate iTunes, I do too, I just can't find a better replacement right now
*with rockbox, you can just use your file-manager to copy over files...*
> **Raineer said:**
> Rockbox can do whatever you want with it.
*here, here!*
> **Raineer said:**
> Basically all I do is just manage my music collection with Amarok, and rysnc it to my iPod.  If I need to add/remove specific files it's as easy as going to Nautilius to manage my collection fast.
[i]i have a very light-weight install (server+openbox), so i just use easytag to keep things clean and xfe to move files.
the best advice is to read all the docs you can on [rockbox]("http://www.rockbox.org/") and then play around with it.  even if your gen ipod isn't yet covered (like the 2gen nano), it may be soon so check back there regularly.  once i went rockbox, i never went back.[/i]

---

### Post by kasperbs on 2007-07-03
> You must watch a lot more video podcasts than I'd have time for in a day
Yeah I know but I also have a girlfriend and at the moment she's working in her holiday 8 hours a day, and thats a lot of time to watch video :)
> with rockbox, you can just use your file-manager to copy over files...
yeah Rockbox does sound like a good alternative, but just like songbird it lacks some of the featrures Im looking for. But I'm sure it will be a good alternative in the futurs, and I will definately be on the look out, and as soon as I can I'm going to ditch iTunes for Songbird, and apple for rockbox. Im just waiting :)

---

### Post by vexorian on 2007-07-03
Please as a customer, request apple to make an itunes port for Linux. They shouldn't really force you to stick to an operating system of THEIR choice.

--
When I connected my ipod something called rythmbox popped out? I think it works well for organizing music...

---

### Post by coolen on 2007-07-04
> **vexorian said:**
> Please as a customer, request apple to make an itunes port for Linux. They shouldn't really force you to stick to an operating system of THEIR choice.

--
When I connected my ipod something called rythmbox popped out? I think it works well for organizing music...

Oh god, please don't. Porting iTunes to Windows was bad enough.
Rhythmbox is the Ubuntu default music player. It can read your iPod database, and play the music...but I don't think it does syncing. Use gtkpod for that (I think you'll find it far easier to use than iTunes, unless you really want every piece of music you own on there. Even so, it wouldn't be that difficult, if you've organised your music well).

---

### Post by kasperbs on 2007-07-04
> Please as a customer, request apple to make an itunes port for Linux
Done!
> Rhythmbox is the Ubuntu default music player. It can read your iPod database, and play the music...but I don't think it does syncing
or manage podcasts well, and not to mention video podcasts which isn't supported at all.
And the id3 tagging is of questionable quality. Either can it organize your files.

At least if suggesting alternatives go with something that come close to iTunes like Songbird, Banshee or Amarok

Just as a side not, I actually read last day that iTunes was among the most missed applications in Linux, so I can't be the only one that like it, even though its not open source.

---

### Post by sab0403 on 2007-07-04
> **kasperbs said:**
> At least if suggesting alternatives go with something that come close to iTunes like Songbird, Banshee or Amarok.

Which one would you recommend, btw? I use Gnome, so I assume Amarok is out of the question...

What I want is a clean, simple interface to organize my playlists. I tried gtkpod already but either it didn't recognize my playlists or I didn't know where to look - it just showed my entire music library. I'd like to have the ability to subscribe/manage podcasts as well, but since I don't use them often to begin with, I can live without them. But I do need the playlist managing.

---

### Post by Nekiruhs on 2007-07-04
> **sab0403 said:**
> Which one would you recommend, btw? I use Gnome, so I assume Amarok is out of the question...

What I want is a clean, simple interface to organize my playlists. I tried gtkpod already but either it didn't recognize my playlists or I didn't know where to look - it just showed my entire music library. I'd like to have the ability to subscribe/manage podcasts as well, but since I don't use them often to begin with, I can live without them. But I do need the playlist managing.
KDE Apps run on Gnome too. I used AmaroK on Gnome before I switched to KDE. If you must have a Gnome app then use Exaile. Its like AmaroK, but written for Gnome. I personally don't like it as much as AmaroK though. I got addicted to the context view and self rating songs.

---

### Post by sab0403 on 2007-07-04
But which one is better to use with the iPod? Is Amarok clearly superior to the others?

Thanks.

---

### Post by notwen on 2007-07-04
> **moore.bryan said:**
> [I]the solution is [rockbox]("http://www.rockbox.org/").
;-)
[/I]

I've read on the rockbox site/forums that there's a chance that I could listen to my iPod(running rockbox) through my Alpine receiver in my truck, but I likely wouldn't be able to control the iPod itself(fwd, rev, stop, etc).  I was wondering if there were any updates on this as of late?  I love the ability of dragging/dropping mp3s to my iPod and being done w/ it.  I used Xplay back when I used windows and it was a great feature and totally eradicated my need of iTunes.  I'm still looking for a simple drag&drop app that would allow me to transfer mp3s from my PC to my iPod w/o a monstrous GUI.  Any ideas? =]  TIA

---

### Post by Nekiruhs on 2007-07-04
> **sab0403 said:**
> But which one is better to use with the iPod? Is Amarok clearly superior to the others?

Thanks.
From my experience it is. Its the easiest way to sync it in my opinion.

---

### Post by sab0403 on 2007-07-04
Sounds good. I've reviewed the web sites of the three, and while Songbird's interface (and foundation, since it's apparently based on Mozilla) impressed me, the fact that you can't rip CDs is pretty limiting.

I still don't like Amarok's visuals, though. Is it customizable?

---

### Post by Nekiruhs on 2007-07-04
> **sab0403 said:**
> Sounds good. I've reviewed the web sites of the three, and while Songbird's interface (and foundation, since it's apparently based on Mozilla) impressed me, the fact that you can't rip CDs is pretty limiting.

I still don't like Amarok's visuals, though. Is it customizable?
Very. There are tools to use new themes for AmaroK if you use Gnome, and the  sidebar is customizable. You can also choose custom colors aswell.

---

### Post by kasperbs on 2007-07-04
> Very. There are tools to use new themes for AmaroK if you use Gnome, and the sidebar is customizable. You can also choose custom colors aswell.
I must warn you here. very is the wrong word, when talking asbout customization. compared to for example songbird the customization is very limited. You can only customize the context sidebar, and the colors you can change only involes certaind features. I hate this as well you can really cutomize amarok apart from the context menu.

Nut it is the best music management tool for linux and good for syncing playlists and music to ipod. maybe it's ok to sync podcasts as well if you dont care about video podcasts.

---

### Post by sab0403 on 2007-07-04
Hmm. Interesting...

Well, I'm going to install it. Can you tell me what tools do I need to customize it in Gnome?

Thanks.

---

### Post by sab0403 on 2007-07-04
Also, should I install from the add/remove, from the Kubuntu version on amarok's website, or from source? Considering I'm going to run it in Gnome...

---

### Post by Nekiruhs on 2007-07-04
Funny, I alwasy thought of Songbird as not very customizable. The only themes it has are White and Black.  And as far as Nut goes, best is subjective.
I attached a Screenshot of my Amarok.
[IMG]http://ubuntuforums.org/attachment.php?attachmentid=37309&d=1183575647[/IMG]

---

### Post by coolen on 2007-07-04
> **sab0403 said:**
> Also, should I install from the add/remove, from the Kubuntu version on amarok's website, or from source? Considering I'm going to run it in Gnome...

Always go for a repository, if the option exists. APT deals with any kind of software...not just Gnome software. KDE is just as big a part of GNU/Linux as Gnome.

---

### Post by vexorian on 2007-07-04
> Oh god, please don't. Porting iTunes to Windows was bad enough.
If you mean that Apple porting it to itunes allowed people to use it and if that didn't happen we wouldn't be losing our time on this discussion then you are right.

If you mean that "because of it being ported to windows it cannot integrate 100% well on OSX"  then you are wrong, blame apple for ineptitude if they can't have 2 different interfaces for the same program...

---

### Post by coolen on 2007-07-04
> **vexorian said:**
> If you mean that Apple porting it to itunes allowed people to use it and if that didn't happen we wouldn't be losing our time on this discussion then you are right.

If you mean that "because of it being ported to windows it cannot integrate 100% well on OSX"  then you are wrong, blame apple for ineptitude if they can't have 2 different interfaces for the same program...

No, I just mean it's a horribly bloated program that only makes sense in a horribly bloated environment where it can integrate properly.
There are other (and better) programs to work with your iPod. For that matter, there are other and better mp3 players available.
I personally don't mind losing time on this discussion. This is my day off ^_^

---

### Post by vexorian on 2007-07-04
All right, in that I agree.

But I guess the problem here is that even if we had a very good alternative in Linux, it wouldn't have the ability to buy stuff.

And I think that most people like it because of that (although I don't see the point)

---

### Post by coolen on 2007-07-04
> **vexorian said:**
> All right, in that I agree.

But I guess the problem here is that even if we had a very good alternative in Linux, it wouldn't have the ability to buy stuff.

And I think that most people like it because of that (although I don't see the point)

I can see the appeal of that (although I purchase all my albums whole). From the look of it, Rhythmbox has a few plugins for various online stores.
Perhaps we could pressure Apple to open up the iTunes store. If they're not making money off of us for using their OS, they may as well profit from our aural fixation.

---

### Post by kasperbs on 2007-07-05
> Funny, I alwasy thought of Songbird as not very customizable. The only themes it has are White and Black. And as far as Nut goes, best is subjective.
Thanks for posting your screenshot, this allows me to explain the thing better. In AmaroK you can only theme the context bar the one you see on the left, the others can not be, here for exmple "Collection" "Playlists" "Files", furthermore you can only change some of the colours in Amarok, which means colors like black or yellow will look bad because some of the original blue colors will still be in there.

Songbird on the other hand is fully customizable. If you dont like any of the themes available you can make your own, (something you cant in amaroK, apart from the context bar). And since songbird is still under development I'm sure there will be many more themes available in the future.

But now you have got some inputs and its up to you to decide. And if you only want the context bar to be themed (like me) then AmaroK is good enough for you.

---

### Post by MockY on 2007-08-03
> **moore.bryan said:**
> [I]the solution is [rockbox]("http://www.rockbox.org/").
;-)
[/I]

Would that solve the issue with transferring playlists. I use Rhythmbox and it does everything I want it, as well as look the way I want a player to look, but there is no support for transferring playlists. With that feature enabled, there is absolutely no reason for the need for iTunes but I have yet to see any reasonable player doing that (Amarok is extremely bloated and not close to as easy to use and therefore not an option). I have waited over a year for such support but yet nothing. 

Does anyone know if this is in the works?

---

### Post by fastpakr on 2007-08-03
I'm curious - what do you not find 'easy to use' in Amarok?

---

### Post by moredhel on 2007-08-04
> Amarok is extremely bloated

That's complete rubbish, it's less demanding in resources than rhythmbox and many other players like banshee etc.

---

### Post by MockY on 2007-08-10
Regardless, it does not answer the question if Rhythmbox does support transferring of playlists and if not, is such support planned?

---

### Post by misfitpierce on 2007-08-10
Songbird gives an amazing replica of itunes with more plugins and tons of great tools/features... Its my number 1...

---

