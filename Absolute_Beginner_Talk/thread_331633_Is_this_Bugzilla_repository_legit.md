---
title: "Is this Bugzilla repository legit?"
date: 2007-01-04
forum: Absolute Beginner Talk
---

### Post by ricardisimo on 2007-01-04
My comp reported a bug automatically to Bugzilla, from whom i received a reply to get a stack trace by installing the appropriate debug tool from "deb [http://people.ubuntu.com/~pitti/ddebs](http://people.ubuntu.com/~pitti/ddebs) edgy main universe". I went ahead and added this repo to my sources.list, but synaptic warned me on each application that the source was not authenticated, that a malicious person might be able to pants me, or give me a wedgie, or some such. Anyhow, are they legit or no? and why wouldn't they have been authenticated by now? Thanks.

---

### Post by taurus on 2007-01-04
My philosophy is when in doubt, don't include it!  Better be safe than sorry...

p.s. Wedgie is so baaad...  ](*,)

---

### Post by d3v1ant_0n3 on 2007-01-04
I thought you got that warning (the untrusted repo one, not the wedgie one) whenever you didn't have the key for a repo? I might be wrong here tho.

I'm sure I've had the same warning from Tr3v's beryl repo when I forgot to re add the key after a reinstall.

---

### Post by ricardisimo on 2007-01-04
> **d3v1ant_0n3 said:**
> I thought you got that warning (the untrusted repo one, not the wedgie one) whenever you didn't have the key for a repo? I might be wrong here tho.

I'm sure I've had the same warning from Tr3v's beryl repo when I forgot to re add the key after a reinstall.

How does one get a key? Is that case-by-case or fairly standard? I want to play along as much as possible when it comes to all things Linux, especially simple stuff like bug reporting, but all it will take is one person telling me to drop this particular baton and I will.

---

### Post by Nonno Bassotto on 2007-01-10
Don't panic. The message you got just means the following. Repositories can be authenticated. This way you are sure that the packages you get come from where you think they are coming from.

To get the sign of a repository you enter a command like
```

wget http://keyaddress.gpg -O- | sudo apt-key add -

```
where you put the real address of the key in place of keyaddress.

So you have to know the address of the key of your repository. I can't help for this: usually where you get instructions to add a repository you also get this information.

---

### Post by ricardisimo on 2007-01-10
Thank you!

---

