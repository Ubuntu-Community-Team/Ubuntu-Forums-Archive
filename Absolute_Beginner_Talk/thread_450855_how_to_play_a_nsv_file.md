---
title: "how to play a nsv file?"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by ubunter1 on 2007-05-21
i downloaded a sports event that was a nsv file,its a winamp file i guess, i cant use any player to play it,vlc sound but no video,mplayer errors,real player nothing,xine nothing,democracy tv nothing,my question is there a codec i can use to play this file and how would i install it?.thanks for any help.

---

### Post by fakie_flip on 2007-05-21
Is that a skate park in your picture? Looks fun!

I found the answer to your question easily by searching the forum. I'm sure I could have found the answer by search google for "nsv linux" as well. Use vlc player. Before you are able to install vlc using the command below, you must have the universe repository enabled on your system. MPlayer also works. You should not install anything with Wine to play nsv videos because there are many native apps for Linux that can do it.

```
sudo apt-get install mplayer
```

or

```
sudo apt-get install vlc
```

---

### Post by apunc1 on 2007-05-21
hmm
it seems you should be able to play the file with those players you listed

i did find a plugin for real player
[http://rnsv.hit.bg/](http://rnsv.hit.bg/)

or you can try this
[http://www.radiotoolbox.com/sc_nsv/](http://www.radiotoolbox.com/sc_nsv/)
its a tar.gz

or maybe this
[http://www.scvi.net/nsv_linux.htm](http://www.scvi.net/nsv_linux.htm)

good luck

---

### Post by ubunter1 on 2007-05-21
> **fakie_flip said:**
> Is that a skate park in your picture? Looks fun!

I found the answer to your question easily by searching the forum. I'm sure I could have found the answer by search google for "nsv linux" as well. Use vlc player. Before you are able to install vlc using the command below, you must have the universe repository enabled on your system. MPlayer also works. You should not install anything with Wine to play nsv videos because there are many native apps for Linux that can do it.

```
sudo apt-get install mplayer
```

or

```
sudo apt-get install vlc
```

the skatepark is in hong kong,i was there 2 years ago now,fun as hell and all to myself!.

i use both vlc and mplayer already and they dont work,i used the search thread on these forums and can find no answer though.the only wine program i use is utorrent.thanks.

---

### Post by ubunter1 on 2007-05-21
> **apunc1 said:**
> hmm
it seems you should be able to play the file with those players you listed

i did find a plugin for real player
[http://rnsv.hit.bg/](http://rnsv.hit.bg/)

or you can try this
[http://www.radiotoolbox.com/sc_nsv/](http://www.radiotoolbox.com/sc_nsv/)
its a tar.gz

or maybe this
[http://www.scvi.net/nsv_linux.htm](http://www.scvi.net/nsv_linux.htm)

good luck

i will try those links you mentioned, thank you,also how do i install the tar.gz with the terminal?,ive looked at the documentation and nothing concrete comes up,id like to learn how to do this for other applications as well.thanks for the help.

---

### Post by apunc1 on 2007-05-21
> **ubunter1 said:**
> how do i install the tar.gz with the terminal?

[http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

---

### Post by fakie_flip on 2007-05-21
> **ubunter1 said:**
> the skatepark is in hong kong,i was there 2 years ago now,fun as hell and all to myself!.

i use both vlc and mplayer already and they dont work,i used the search thread on these forums and can find no answer though.the only wine program i use is utorrent.thanks.

sure they work. they work just fine for me and other users on this forum, but with the very minimal information you gave us, there is no way for us to know what the problem is. for example, you have not told us what happens and what errors you get.

---

### Post by ubunter1 on 2007-05-21
> **fakie_flip said:**
> sure they work. they work just fine for me and other users on this forum, but with the very minimal information you gave us, there is no way for us to know what the problem is. for example, you have not told us what happens and what errors you get.

in my first post i said vlc plays sound but no video,mplayer ,error initializing/opening the selected video out(vo)device.xine nothing happens,real player-does not have capabilities to play back,components required is nsv.my main question is how to play a nsv file with a player. the standard players dont work,i have them all,are there special codecs that winamp have that these dont?.

---

### Post by ubunter1 on 2007-05-21
> **apunc1 said:**
> [http://www.monkeyblog.org/ubuntu/installing/#source](http://www.monkeyblog.org/ubuntu/installing/#source)

thanks for the info.will do.

---

