---
title: "Grip lost its magic - what's up? (Dapper)"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by RH9R on 2007-04-23
Built new box & the Asus mboard has alot more trouble than the old microstar. MSI install detected everything. The Dapper disk didn't detect printer, couldn't do easyubuntu, etc.
 
Grip was wonderful. I followed MetalMusicAddict's fine thread about configuring Grip. I did that again, and now all files produced by several configuration settings produce only a file of 2.1K
 
One warning on the grip install was that 3.3.1-4 was the latest - download earlier version if you have trouble. I don't seem to be able to view any package version earlier than the 3.3.1-4.
 
Has Grip version changed in the last 6 mo? Anyone else having the problem? 
 
The dumb noob appreciates your help.

---

### Post by zorkerz on 2007-04-23
Im not entirely sure what you are looking for here. What release are you using?

Im in feisty and the repos have version 3.3.1-11. You could try the new version but it might have different dependencies and is not guaranteed to work. The feisty deb is here [https://launchpad.net/ubuntu/gutsy/+package/grip](https://launchpad.net/ubuntu/gutsy/+package/grip)

Should be somewhere you can find a deb of the older one or you could try and compile it yourself. Come back and say some more then we will have a better idea of how to help.

cheers

---

### Post by RH9R on 2007-04-23
On Dapper, the Synaptic version of Grip (w/ software preferences set to fetch the latest version) is 3.3.1-4
 
On my last box, it installed and ran like a hose. Now, every ripped & encoded file winds up 2.1k, and doesn't play. This is from a purchased CD. 
 
'Gladly supply any detail (as much as a noob can find). Lame is installed.  If there's any detail that is relevant, I'll chase it. 
 
Thx again for the reply.

---

### Post by zorkerz on 2007-04-23
do you need to use grip? I use the default sound juicer that seems to work ok?

What file format  are you trying to rip the music to? I would recommend .ogg as it is the default and entirely open source (also many will claim has the best quality per bitrate though i don't tell the difference).
 Other file formats in the long run could cause you trouble but if you don't loose the cds it should not matter.

Im still a little confused is your ultimate goal to be able to rip cds to your computer or is this just part of it?
cheers

---

### Post by RH9R on 2007-04-24
Zorkerz, Thank You for your reply.
 
Grip was recommended in one Ubuntu book, and I found I liked it alot. I've been ripping to mp3 format, I suppose there's nothing sacred about that, but few mobile players can play it. I thought mp3 would be best for its universality & portability. I have the orig. discs for much of the music, but not all. Most was ripped to .ogg format - before I found Grip. 
 
If mobile players & other machines can play .ogg, there's no need for mp3, but until that's true, I'd like to keep the ability to rip to mp3.
 
SoundJuicer also has little control over bitrates, etc. Grip is pretty fully configurable. 
 
Again, I appreciate your help.

---

### Post by MetalMusicAddict on 2007-04-24
I'd honestly do a clean install of Feisty. Your HW support will be alot better and multimedia support is better. Thanx for using the GRIP guide. ;)

As for your question here I have no clue. :(


EDIT:
Actually, the more I think about it I think I have seen this and it was a config issue.


TIP - Show the hidden files in your home dir and save the files marked .grip. You'll see 'em. Ive done this since Dapper with no issue.

---

### Post by zorkerz on 2007-04-24
Yes you are right sound juicer is a pain in terms of settings. My impression is that you can set most things by creating new profiles but then you must know how to set the GStreamer pipeline.

You are also right with ogg. It is sadly not supported and your friends will get made if they can't play songs over the network from you computer. 

I think i might give grip a try in feisty.

---

### Post by RH9R on 2007-04-25
[QUOTE=MetalMusicAddict;2523420]

EDIT:
Actually, the more I think about it I think I have seen this and it was a config issue.


MMA, You're right!! \\:D/  I just went through your config thread again, and found one option w/ lower instead of upper case option and one other parm. missing. 
 
MMA. They are MIGHTY!, and hang LOW!! 
 
Thank You very very much!! The Noob appreciates your help!
 
I'm conflicted about the move to Feisty. Prob reports spook me, as I'm not that skilled technically. 'Trying to lose my ignorance daily, but its slow.

---

