---
title: "Manjaro - pacman"
date: 2018-04-18
forum: Arch and derivatives
---

### Post by anon_private on 2018-04-18
Hello,

I though that I would install TOR.

Octopi tells me that the tor in the repo is version 0.3.2.10-1

The TOR website gives the latest version as 7.5.3, and now 9,0a5.

I thought I would check using pacman

I typed pacman -s tor. The -s is not recognised.

Can  any one comment on the -s, and on the disparity between the tor  versions. It is almost as if tor in the repo, is not TOR the privacy  programme.

Thanks

---

### Post by Dennis N on 2018-04-18
> I typed pacman -s tor. The -s is not recognised. Can any one comment on the -s, and on the disparity between the tor versions.Can any one comment on the -s, and on the disparity between the tor versions.

The 's'  option should be a capital letter 'S'

```
sudo pacman -S mousepad
```

Tor broswer is apparently not in the Manjaro repos. tor in the repositories is an unrelated package. You will have to get the browser elsewhere.

---

### Post by anon_private on 2018-04-18
sudo pacman -S tor works. I am sure that you are right. But how do you know that the tor in the repo is not the onion router and with its own browser. Evidently --search is also an option. I found pacman --search, or --Search seems invalid!

It is probably best to get the bundle from TOR

---

### Post by Dennis N on 2018-04-18
> I am sure that you are right. But how do you know that the tor in the repo is not the onion router and with its own browser.

No, I think I was actually wrong. I looked again more carefully and that package must be something related to a (the?) Tor browser. The brief description in Manjaro's 'Add/Remove Software' application calls it an 'anonymizing overlay network' and doesn't use the term 'browser' or 'web browser' so I assumed (wrongly) it was unrelated. I gather that the Tor Browser is the Tor Project's custom browser configured to use the tor package. So the package (tor) is not by itself a browser, and the Tor browser is not in the repositories. There is a link to the Tor project in Manjaro's 'Add/Remove Software' screen for tor so that seems to confirm it.

---

### Post by thenailedone on 2018-04-19
Perhaps have a look at the AUR to get the latest and greatest (and everything in between). I personally like to use pamac and I am not well versed in the other package managers (and as I am not currently using Manjaro I can't have a look myself).

---

