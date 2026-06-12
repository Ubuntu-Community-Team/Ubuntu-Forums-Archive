---
title: "SSL Error + Tor = Configure Error"
date: 2007-05-17
forum: Absolute Beginner Talk
---

### Post by Dr Small on 2007-05-17
Greetings,
I am trying to install [tor]("http://tor.eff.org") on another computer, and I'm receiving an error.

I have libevent installed, and openssl, and am running this command to configure it:
```
./configure --with-libevent-dir=/usr/local
```

Here is what the readme says for quick reference:
> If it doesn't build for you:

  If you have problems finding libraries, try
    CPPFLAGS="-I/usr/local/include" LDFLAGS="-L/usr/local/lib" \
    ./configure
  or
    ./configure --with-libevent-dir=/usr/local
  rather than simply ./configure.

  If you have mysterious autoconf failures while linking openssl,
  consider setting your LD_LIBRARY_PATH to the openssl lib directory.
  For example, "setenv LD_LIBRARY_PATH /usr/athena/lib".

Ok. Now that we understand all of the basics, here is the error that is being outputed to me.

```
checking for OpenSSL directory... configure: error: Could not find a linkable OpenSSL. You can specify an explicit path using --with-ssl-dir
```

Any idea what I could do to get this to work?

Dr Small

---

### Post by Seisen on 2007-05-17
Why don't you just install it using Synaptic or apt-get?

---

### Post by Dr Small on 2007-05-17
Because it is an old version on the repositories and only works part time. I want the newest version, that works when I need it.

Dr Small

---

### Post by Seisen on 2007-05-17
Actually if you go to the tor website the repo's should have the new tor and privoxy

[http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian]("http://wiki.noreply.org/noreply/TheOnionRouter/TorOnDebian")

---

### Post by Dr Small on 2007-05-17
I guess i could try that, although I have installed tor this way on my other ubuntu system, and I really wanted to figure out how to install it this way again. Don't know why, but I love doing things the hard way :D

Dr Small

---

### Post by FakeOutdoorsman on 2007-07-01
I had this same problem and realized that I needed to install the ssl development files: libssl-dev.
```
sudo aptitude install libssl-dev
```

...and then try to compile:
```
./configure && make
```

---

