---
title: "SYNAPTIC and proxy that requires authentication"
date: 2006-01-02
forum: Absolute Beginner Talk
---

### Post by GregM on 2006-01-02
I have synaptic packet manager configured to use my proxy (url/port number) however my proxy requires authentication. How can I push userid/p-word? (Synaptic doesn't ask for it, nor do I see a place to enter it. 

Any help is appreciated!

---

### Post by cwaldbieser on 2006-01-02
[QUOTE=GregM]I have synaptic packet manager configured to use my proxy (url/port number) however my proxy requires authentication. How can I push userid/p-word? (Synaptic doesn't ask for it, nor do I see a place to enter it. 

Any help is appreciated![/QUOTE]
Settings -> Preferences -> Network.

For apt-get, you can put the following in your ~/.bashrc file:
```

export HTTP_PROXY=http://uid:pwd@proxy-server:port
export http_proxy="$HTTP_PROXY"

```

---

### Post by Darth Vadrouille on 2006-01-11
I think you can use the uid:pwd@proxy-server:port format in Synaptic too (as posted previously, go to Settings / Preferences / Network for proxy settings)

---

### Post by kolesarm on 2006-10-07
genius! been wondering for the whole afternoon how to send the username and passwd. now its working for me too - [http://www.ubuntuforums.org/showthread.php?t=273014]("http://www.ubuntuforums.org/showthread.php?t=273014")

thanks!

---

