---
title: "Cannot play VCD in Ubuntu Movie Player"
date: 2007-05-16
forum: Absolute Beginner Talk
---

### Post by swarup on 2007-05-16
Ubuntu's Movie Player does not recognize VCDs. Someone told me to download gstreamer0.8.misc which I did and it installed. But I don't even know where the application went. And it doesn't make any difference-- Movie Player still does not recognize my VCDs, which play just fine in Windows 98. How can I get it to work in Ubuntu 7.04?

---

### Post by starcraft.man on 2007-05-16
Easy way to make sure you can play all media content is to install all the codecs. Easy to do also.

Please follow this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to enable extra repos, and then this [one]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") to install extra codecs.  You'll want to run both rows of code (the gstreamer and w32 one in the terminal).

And just in case, Terminal is at Applications > Accessories > Terminal.

Should get ya working with all media. I believe that covers every codec. If your not using feisty, there are similar sections in every version of the Ubuntuguide in my sig :).

You may also want to install VLC, I like it as a player and I think it plays a few real oddball formats not even covered in the codecs, I could be wrong though >.>.

---

### Post by TheMono on 2007-05-16
OK, first off, Gstreamer is not an application. Think in terms of Windows Media Player, and how you install codecs for it so it can play other formats. Gstreamer is kind of like a behind the scenes thing that allows the move player to use different formats - so you don't run Gstreamer, you install Gstreamer stuff in order to enhance the movie player.

Second, the version of Gstreamer we use is 0.10, not 0.8, so that package you installed will have done nothing really - you may as well remove it again.

Thirdly, to get it to play, try installing 
gstreamer0.10-plugins-good
gstreamer0.10-plugins-bad
gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad-multiverse
gstreamer0.10-plugins-ugly-multiverse

If these don't work, then go to the Medibuntu website ([http://medibuntu.sos-sts.com/](http://medibuntu.sos-sts.com/)) and follow the instructions there to add their extra repository, which will allow you to play even more formats again.

---

### Post by swarup on 2007-05-16
> **starcraft.man said:**
> Easy way to make sure you can play all media content is to install all the codecs. Easy to do also.

Please follow this [guide]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_add_extra_repositories") to enable extra repos, and then this [one]("http://ubuntuguide.org/wiki/Ubuntu:Feisty#How_to_install_Multimedia_Codecs") to install extra codecs.  You'll want to run both rows of code (the gstreamer and w32 one in the terminal).

And just in case, Terminal is at Applications > Accessories > Terminal.

Should get ya working with all media. I believe that covers every codec. If your not using feisty, there are similar sections in every version of the Ubuntuguide in my sig :).

You may also want to install VLC, I like it as a player and I think it plays a few real oddball formats not even covered in the codecs, I could be wrong though >.>.

I went to the first guide you indicated, for adding extra repos. But where it says "This is the recommended way to do it:........"  ---there is nothing there, following the colon!!
And then the other way, which is "at your own risk", looks awfully difficult.

Anyway, I have all the main four boxes already checked, for main, universe, restricted, and multiverse. Is that enough?

---

### Post by kwidzin on 2007-05-19
I'ts bug of Feisty's hal package I think. Codecs installations isn't right solution of this problem.

---

