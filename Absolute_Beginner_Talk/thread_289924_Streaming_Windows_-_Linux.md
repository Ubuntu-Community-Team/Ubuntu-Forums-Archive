---
title: "Streaming Windows - Linux"
date: 2006-10-31
forum: Absolute Beginner Talk
---

### Post by 4cesmoker on 2006-10-31
I can stream movies/clips from my buddies computer to mine and vise versus. But I can't stream from my windows box. I'm forced to copy the files over to watch them. Can someone please help me or point me in the right direction ?

I like using VLC media player. I have VLC on the XP/OS box.

---

### Post by tshirtz1013 on 2006-10-31
I have edgy on my machine and a xp media box in my front room, I also have a dapper box and a dapper laptop, the ubuntu machines have no problem streaming video content from each others drive. Yet even though I can see the windows shares, I cant stream them through any media player either, on any of the ubuntu boxes. I am forced to copy the file over and play it directly. I saw some settings in VLC but they appear to be only for becoming a streaming server. I think we have the same issues. Let me know if you find out the solution, I would gladly change the xp box over if it was not for the rest of the household.

---

### Post by RTB-UK on 2006-11-30
I also have this issue. I did somthing which fixed it in one of my previous installs. The problem is i think that the media players cannot resolve the samba adresses. E.g

smb://windowsPC/videoFolder/videoFile.avi

The media player doesn't know where too look for that path. I have no idea how to fix this however.

---

### Post by tronica on 2006-11-30
you need to mount the windows share, 


cd /mnt
sudo mkdir winshare
sudo chmod777 winshare
sudo mount -t cifs //ipaddress/sharename /mnt/winshare -o user=usernameofwindowsbox,pass=password

---

