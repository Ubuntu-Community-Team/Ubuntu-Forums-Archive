---
title: "TAR.GZ related question"
date: 2007-09-01
forum: Absolute Beginner Talk
---

### Post by Holy Knight on 2007-09-01
I wanted to install Compiz Fusion and Firefox 2.0.0.6 but after downloading it from the site(Compiz not available in the repository) I get a tar.gz file.

Can anyone tell me the easiest way of installing these programs?I looked at the forums but no satisfactory answer,

Cheers

---

### Post by s26c.sayan on 2007-09-01
Try using the 3rd party  [Trevino's repositories]("http://3v1n0.tuxfamily.org/"), instead of downloading source packages!

Follow this : [http://ubuntuforums.org/showthread.php?p=2895086](http://ubuntuforums.org/showthread.php?p=2895086)

---

### Post by Majorix on 2007-09-01
```
cd /path/to/directory/containing/the/file
tar -zxvf filename
cd newDirectory
./configure
make; sudo make install
```

should work for most sourcecodes. I am sure this has been told numerous other times though, next time look a bit more careful ok? ;)

What I can suggest is though, after the part in the code I pasted, go to that new directory in Nautilus and try to find a ReadMe telling how to compile it (configure make sudo make install is the usual way but there can be some exceptions) or even an executable file (who knows, maybe they just decided to compress the working file).

Good luck.

---

### Post by Billy_McBong on 2007-09-01
[COLOR="Blue"]you could add Treviño’s eyecandy repository.
 go into synaptic > settings > repositories > 3rd party software and add ```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

then click the reload button, compiz-fusion will be there. it will also be much easier to update it if you install it this way[/COLOR]

---

### Post by Holy Knight on 2007-09-02
> **Billy_McBong said:**
> [COLOR="Blue"]you could add Treviño’s eyecandy repository.
 go into synaptic > settings > repositories > 3rd party software and add ```
deb http://download.tuxfamily.org/3v1deb feisty eyecandy
deb-src http://download.tuxfamily.org/3v1deb feisty eyecandy
```

then click the reload button, compiz-fusion will be there. it will also be much easier to update it if you install it this way[/COLOR]

I followed your method but this error poped out:

```
W: GPG error: http://download.tuxfamily.org feisty Release: The following signatures couldn't be verified because the public key is not available: NO_PUBKEY 2D6CFB44DD800CD9
```

What does it mean?:confused:

---

### Post by s26c.sayan on 2007-09-02
The repository is digitally signed by the creator! You'll need the GPG public key in your keyring.

```
sudo wget [http://download.tuxfamily.org/3v1deb/DD800CD9.gpg](http://download.tuxfamily.org/3v1deb/DD800CD9.gpg) -O- | sudo apt-key add -
```

Everything is explained step by step in the [link]("http://ubuntuforums.org/showthread.php?p=2895086") I provided in my previous post!

---

### Post by por100pre1 on 2007-09-02
You need the GPG key for that repo. Look for it [here]("http://ubuntuforums.org/showthread.php?t=526665").

EDIT: Too late!!!

---

