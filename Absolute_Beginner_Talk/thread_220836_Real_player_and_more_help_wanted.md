---
title: "Real player and more help wanted"
date: 2006-07-22
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2006-07-22
I am still hanging in here !! To date  Steaming mp3 ok ...Mp3 ok ..Mpeg ok

Just peal player ( and winamp would be nice .. )

Real player for the bbc !! need that !.  Trouble is Real player is a bin file ..I read the other thread on bin files managed to create a folder in
 /usr/share/.......called realplayer....

ie   /usr/share/realplayer

now I put the Realplayer10GOLD.bin file in desktop,   but I couldnt copy or open 

 terminal says   root/home/s# cd /usr/share/realplayer
                 root/home/usr/share/realplayer#   

Actually I rephrase this How do I ..1. get permission chmod??? to copy to my new folder
     2; open the bin file ( in ubuntu I just clicked on it but I am using xubuntu ) 
     run synaptic to install the new program ( or make a launcher)


Lastly Winamp for Linux is a Rpm file ,,Can I swap rpm files to deb files???


Other than that all is working well now ..nice little package this ..

Oh last thing is there a quick kill for programs that lock up the cpu ,,,I did  sudo su ps in order to find number to kill it ,,but the program wasnt listed ( window equiv of task manager ...)


Sorry for all the above ...If I can nail that ,,I am home and hosed ...Running free as it were 

Oh and I love the way I can change languages at the start ,, In windows some fonts are changed ,,and the rest are unreadable ,,but here EVERYthing has changed ..absolutely fantastic that is ..I can install Japanese harware without guessing !!!:p 


Thank everyone ( for putting up with the raving of a loon )

Kind regards Stephen

---

### Post by RRS on 2006-07-22
Add the new commercial repository to your sources list.
```
deb http://archive.canonical.com/ubuntu dapper-commercial main
```
You'll then be able to install Realplayer from synaptic.

Also check this site; [http://monkeyblog.org/ubuntu/installing/]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by ajgreeny on 2006-07-22
You can install *realplay* (not *realplayer* which is a different version)from the repositories without problems and that will let you play BBC programmes in Firefox, not sure about other browsers.  You will need to have the extra repositories activated for synaptic or apt-get to do the job but otherwise all should work OK.

Look in *about:plugins* in Firefox and see which real plugins you've got;  I have:-
File name: /usr/lib/mozilla/plugins/mplayerplug-in-rm.so
File name: /usr/lib/mozilla/plugins/nphelix.so
but I admit I dont know which is actually used for the BBC online; I think it's the first one (mplayerplug-in rm.so).

I have also added the BBC URL's as favourites in Realplayer so I don't even need a browser running to listen to BBC Radio.

Instead of using winamp, why not have a look at xmms, which is a linux equivalent and open source.

---

