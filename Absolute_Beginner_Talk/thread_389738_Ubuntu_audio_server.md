---
title: "Ubuntu audio server"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by rustybones on 2007-03-21
Hi guys, first time poster, long time reader.

My question is this:

I have a Ubuntu machine running 6.10. What I want to do is have my Windows XP SP2 machine to be able to able to listen to music off it. 

I did have mt-daapd/Firefly running and machines on my LAN could see and listen to the audio off it via itunes. Thing is I upgraded mt-daapd to the latest nightly which then broke the share and itunes can no longer see it.

**Also** I really don't want to use itunes to listen to my music, I would rather something like Foobar or Musikcube or Winamp. Winamp does have a very alpha plugin to use DAAP but all it would serve up is 40 tracks.

Does anyone have suggestions about how I would achieve this? Has anyone else struck similar problems or am I the only newbie who is spastic enough to not be able to sort it out?

cheers guys & gals

---

### Post by lassegs on 2007-03-21
I would recommend gnump3d if you want an easy way to do this. 
It indexes your music files, then lets you access them through an ok (bit ugly) gui on your browser. No need for apache or any database.

Check this out:
[http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_GNUMP3d_for_Streaming_Media_Server_service](http://ubuntuguide.org/wiki/Ubuntu_Edgy#How_to_install_GNUMP3d_for_Streaming_Media_Server_service)

If you want something a bit more sophisticated, you could try kplaylist. It needs apache and php. 
[http://www.kplaylist.net/](http://www.kplaylist.net/)

---

### Post by afoglia on 2007-03-30
> **rustybones said:**
> I have a Ubuntu machine running 6.10. What I want to do is have my Windows XP SP2 machine to be able to able to listen to music off it. 

I did have mt-daapd/Firefly running and machines on my LAN could see and listen to the audio off it via itunes. Thing is I upgraded mt-daapd to the latest nightly which then broke the share and itunes can no longer see it.


Nightlies have a tendency to do that.  If upgrading to a following nightly didn't work, then next thing I'd try is upgrading to Feisty (7.04).  Mt-daapd is one of the distributed packages.  It's an older version, but it's more likely to work.  Feisty's first beta came out last week, and the final release is scheduled to come near the end of April.  (You might even be lucky enough to install it atop your current Edgy setup without upgrading everything else.)

The other option is to go to mt-daapd/Firefly forums and ask them.

> 
**Also** I really don't want to use itunes to listen to my music, I would rather something like Foobar or Musikcube or Winamp. Winamp does have a very alpha plugin to use DAAP but all it would serve up is 40 tracks.

Does anyone have suggestions about how I would achieve this? Has anyone else struck similar problems or am I the only newbie who is spastic enough to not be able to sort it out?


I know MusikCube doesn't support DAAP and won't for a long while.  DAAP-supporting Windows clients are few and far between.  I found a few small projects googling, but nothing that great.

---

