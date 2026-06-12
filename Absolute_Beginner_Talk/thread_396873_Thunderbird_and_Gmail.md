---
title: "Thunderbird and Gmail"
date: 2007-03-30
forum: Absolute Beginner Talk
---

### Post by deafchickadee on 2007-03-30
I installed Thunderbird by typing in the terminal;

```
sudo aptitude install mozilla-thunderbird
```

Is it possible that it might be broken? How do i find out? I just cannot seem the configuration up and running properly even though I've been on the official Gmail configuration site.

Am I better off downloading thunderbird  from Mozilla myself and installing the package into the terminal myself? 
To download it, I note that it is a tar gz file. How can i convert it into a deb folder and install it into my computer.

Evolution works, but I find it rather plain and boring.

---

### Post by h0ax on 2007-03-30
Can you actually run the program?
Generally the install command would be
```

sudo apt-get install mozilla-thunderbird

```


You can install it from tar.gz - you just need to "untar it" (tar -zxvf) then install from source.(./configure, make, make install)
This can be a little more tricky, but we can help

---

### Post by deafchickadee on 2007-03-30
Yes the program is running but the configuration for recieving my emails from gmail is not working.

Server not connecting or doesn't exist or  something to that effect.

---

### Post by deafchickadee on 2007-03-30
And i'll just add..  yes my pop thingy is activated in gmail...

---

### Post by deafchickadee on 2007-03-30
The thunderbird alert says, word for word:

"Mail server does not support secure authencation"

what does that mean?

Anyone?

---

### Post by Big Ben on 2007-03-30
I think this is really more of a question for Mozilla forums rather than Ubuntu, but my best guess is that you have the "Use secure authentication" checkbox checked in the "Server Settings" dialog of your Thunderbird "Account Settings". Try unchecking that box. You should also check the SSL radio button under "Use secure connection".

I sincerely doubt it's a problem with your install of Thunderbird--probably just your account settings.

Here's more info on setting up Thunderbird for Gmail:
[http://kb.mozillazine.org/Using_Gmail_with_Thunderbird_and_Mozilla_Suite](http://kb.mozillazine.org/Using_Gmail_with_Thunderbird_and_Mozilla_Suite)

---

### Post by deafchickadee on 2007-03-30
Hey thanks..  your URL worked.. Thanks heaps!!!

---

