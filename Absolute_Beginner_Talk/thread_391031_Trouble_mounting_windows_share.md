---
title: "Trouble mounting windows share"
date: 2007-03-22
forum: Absolute Beginner Talk
---

### Post by ld50 on 2007-03-22
Ok, I believe I am making a simple error somewhere but I have been unable to solve this....

I am trying to mount a windows share using smbmount, the location of the folder I want to mount is "My Documents/My Music" 

I am able to mount other shared folders that do not contain spaces in thier names just fine, the line I am using is as follows, 
>  sudo smbmount //steve/"my documents"/"my music" /home/kyle/Music
I recieve the following error
> 14904: tree connect failed: ERRDOS - ERRnosuchshare (You specified an invalid share name)
I think I am just typing something wrong here any suggestions?

I might add that the folder is visible to browse from nautalus so it is shared correctly

---

### Post by ld50 on 2007-03-22
Well I kinda fixed it, just changed the "share folder as" name under windows to "Music", works just fine but still seems that there should have been a way to do it otherwise...

---

