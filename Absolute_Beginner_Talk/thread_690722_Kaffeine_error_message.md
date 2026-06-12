---
title: "Kaffeine error message"
date: 2008-02-07
forum: Absolute Beginner Talk
---

### Post by Syndacate on 2008-02-07
Hey,

When I open SOME files I'm getting these 2 error msgs from kaffeine:

[img]http://i82.photobucket.com/albums/j271/Syndacate/Computer%20Stuff/err.png[/img]

It's only sometimes though and it's not with any specific file type - happened with a few .avi files and I just thought they were corrupt during copying - but then it started doing it with this file (which is also .avi) and I checked it with VLC and it opened up no problem.

Note that when I hit the **details >>** button I get this:
```
06:52:57 PM: input_file: File not found: >/media/sdc5/Temporary/<filename>

06:52:57 PM: xine: found input plugin : file input plugin

06:52:57 PM: >>> Check if another program already uses PCM <<<

06:52:57 PM: snd_pcm_open() failed:-19:No such device

```

I can't make much of that error message...I mean it's not really that big of a deal since I can watch the whole series with VLC with one extra click - but like most people, I rather deal with a problem than go around it.

PS:  There is a filename after "Temporary" - I just removed it, figured posting things that can be implied as some crazy *** warez pirate illegal download-copyright infringement fallacy could be self-incriminating.

---

### Post by talsemgeest on 2008-02-08
Go into synaptic and search for xine. Click on the check box and click reinstall.

Hope this helps :)

---

### Post by Syndacate on 2008-02-11
Isn't xine a media player?

They work fine under VLC - I'm just trying to get them to work in Kaffeine :P.

EDIT:
PS:  After looking at the title of the error msgs (which I didn't before) I do feel like a complete retard.

Though I thought Xine was different?

These error msgs are coming from trying to open with Kaffeiene?

::Confused:: :(

---

### Post by talsemgeest on 2008-02-11
I am pretty sure that xine is the backend to both the players: totem and kaffeine. So maybe try completely uninstalling xine and then reinstalling it. And maybe do the same thing with kaffeine as well.

---

### Post by Syndacate on 2008-02-13
> **talsemgeest said:**
> I am pretty sure that xine is the backend to both the players: totem and kaffeine. So maybe try completely uninstalling xine and then reinstalling it. And maybe do the same thing with kaffeine as well.

I think the files themselves are glitched, M player plays it without sound, I can convert them to .avi and they play fine, but the audio is a bit off from the movie, totem doesn't play them at all.

I'm thinking def. messed up movie?  Though it works fine on my friend's windows machine - I'll put it on my windows machine tomorrow 'n see if it still has probs or if it's just this.

The other prob I'm getting with kaffeine is "link not found" or something to that effect with certain movies :( - but it's there.

I can't reinstall Xine, I get this error:

```

$ sudo apt-get install xine
Reading package lists... Done
Building dependency tree
Reading state information... Done
Package xine is not available, but is referred to by another package.
This may mean that the package is missing, has been obsoleted, or
is only available from another source
E: Package xine has no installation candidate

```

---

### Post by talsemgeest on 2008-02-13
Ok it seems that the package is "kaffeine-xine". It is only the engine for kaffeine, not the full player, so you might want to try it with "kaffeine" as well.

---

### Post by Syndacate on 2008-02-14
LoL

I give up.

I reinstall Kaffeine.

Now I don't get the error, I get sound, but no video.

With M player I get an error then video, but no sound.

I guess I'm supposed to run them both at the same time or something ^_^

---

### Post by talsemgeest on 2008-02-14
That is weird...

---

### Post by Syndacate on 2008-02-15
Yeah I gave up, whatever I can't open with Kaffeine I'll just open with VLC.  While I'd like to know what the issue is and fix it, it's not a huge priority.

---

### Post by nvivo on 2008-02-23
I'm having the same problem here.

I just remembered that gutsy-backports updated libxine1 some days ago, and I didn't play anything since then.

I forced the main version, and the error was gone, but the plugins were too and I don't seem to be able to downgrade the plugins.

I'll try to play with apt-get and dpkg and see what I can get.

---

### Post by nvivo on 2008-02-27
Today a new version of Kaffeine was available and it doesn't have this problem anymore.

---

### Post by Syndacate on 2008-02-28
I don't think I got the download update, do you have to manually re-install?

---

