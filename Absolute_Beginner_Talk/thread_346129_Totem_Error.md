---
title: "Totem Error"
date: 2007-01-25
forum: Absolute Beginner Talk
---

### Post by WKnew on 2007-01-25
After installing one of the updates ... when I try to listen to an on-line stream launched from a web site I get the following error:

Totem could not play 'mms://a93.l3072827357.c30728.g.lm.akamaistream.net/D/93/30728/v0001/reflector:27357?auth=caEcebObjdhc3aFaadzdWbUa4czdCaGcYab-bfTFBo-kJa-AoyDMzu=0002'.




caEcebObjdhc3aFaadzdWbUa4czdCaGcYab-bfTFBo-kJa-AoyDMzu=0002'

It means?

Edit: Somebody else posted this solution - sorry I don't recall who it was, but it solved my problem.

"This post is an FYI on how I eventually solved the problem in hopes this will help others.

- close down firefox
- open up a terminal window and: cd /usr/lib/firefox
- backup the plugins directory by: sudo cp -r plugins plugins.bak
- go into the plugins directory: cd plugins
- remove the totem plugins: sudo rm *totem*

This removes the totem plugins and firefox reverts to using the mplayer plugin which works just like it did with dapper."

My radio stream is now plying with the gxine player.

---

### Post by mikewhatever on 2007-01-25
Can't possibly imagine anyone knows what that means. May be, you can post a link to the site, or even the stream that gave that error. Were you able to play videos from that site before?

---

