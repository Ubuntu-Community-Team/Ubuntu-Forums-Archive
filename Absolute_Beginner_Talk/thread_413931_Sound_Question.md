---
title: "Sound Question"
date: 2007-04-19
forum: Absolute Beginner Talk
---

### Post by Darkblizz on 2007-04-19
Getting more than one application to use the soundcard at the same time

    * You might want to play a game and listen to music on your favorite music player at the same time. To do this successfully, you will have to use ALSA since it supports this feature the best. On all the music players I know of, you can configure the sound engine, to any module that is available.

    *
      The setting is usually found under something like Tools >>> Configure >>> Player Engines.

    *
      For games, it is a bit more tricky since there is not always a way to configure the player engine directly. Most games, however, do support the OSS. ALSA has an OSS module that allows OSS applications to use the ALSA driver.

    *
      To do this you will need the alsa-oss package
      Code:

      sudo apt-get install alsa-oss

    *
      After doing this step, it is very easy to use alsa-oss. In the shell, you can type 'aoss' then the name of the program name you want to use with alsa-oss.

K i installed alsa but i dont get how to work the alsa-oss thing  im trying to run xmms and a game at the same time plz help!

---

### Post by leibowitz on 2007-04-25
Don't use xmms anymore if you want to be able to have the sound. I never heard of aoss before and won't use it any time soon. Just use Alsa aware applications. It will be simplier.

Anyway, doesn't xmms have a sound driver selection somewhere in the configuration, where you can choice between alsa and oss ?

---

