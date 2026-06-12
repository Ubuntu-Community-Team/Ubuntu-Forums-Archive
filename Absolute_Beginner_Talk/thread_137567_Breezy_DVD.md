---
title: "Breezy DVD"
date: 2006-02-28
forum: Absolute Beginner Talk
---

### Post by Unoone on 2006-02-28
About the Ubuntu 5.10 dvd. How does one access the universe software repositories on the dvd via synaptic? The Ubuntu facts only give information about adding the web universe repositories to synaptic. What link must you code into synaptic to access the universe software repositories on the dvd. Thanks.

---

### Post by Xian on 2006-02-28
You haven't gotten a response so I'll just offer some input and see if anyone else will chime in. I would imagine the format would be similar to this (as it appears in the apt sources.list):

```
deb dvd:[Ubuntu 5.10 _Breezy Badger_ - Release Info Goes Here]/ breezy main restricted universe
```

---

### Post by Unoone on 2006-03-01
[QUOTE=Xian]You haven't gotten a response so I'll just offer some input and see if anyone else will chime in. I would imagine the format would be similar to this (as it appears in the apt sources.list):

```
deb dvd:[Ubuntu 5.10 _Breezy Badger_ - Release Info Goes Here]/ breezy main restricted universe
```[/QUOTE]

I added this to the source.list. It doesn't work. Error messages pop up in synaptic. The message states that the code is not a valid repository. 

Can you really use the dvd to access universe? I have not seen any information outside of linux magazine ads that say you can do so. Have you used the universe dvd repository has anybody?

---

