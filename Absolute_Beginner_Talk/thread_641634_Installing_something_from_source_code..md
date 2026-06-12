---
title: "Installing something from source code."
date: 2007-12-15
forum: Absolute Beginner Talk
---

### Post by Pogeymanz on 2007-12-15
I'm trying to install Code::Blocks from source codes. Apparently after downloading this stuff I'm supposed to execute this Bootstrap program. When I try that I get an error:" 67: libtoolize: not found." How do I fix that?

---

### Post by mellowd on 2007-12-15
What's the app called?

You might need to so this:

```
sudo apt-get build-dep app-name
```

---

### Post by Pogeymanz on 2007-12-15
Forgive my incompetence. The app is called codeblocks. I use it as a C++ editor. When I use that command you posted, in which directory should I be doing it?

Isn't there just something I can update/install to make that libtoolize thing work? What is that anyway? I never understand what I'm doing. I mostly blindly enter commands when told. At least I'm beginning to understand some of the simple things like cd, get, etc.

---

### Post by RomeReactor on 2007-12-15
Hi. You can install CODE::BLOCKS from Synaptic; Open Synaptic, go to "Settings->Repositories", and in the "Third-Party Software" tab, press the "Add" button. There, enter:
```
deb http://lgp203.free.fr/ubuntu/ gutsy universe
```

Change **gutsy** to **feisty** or **edgy** in case you're using one of those  earlier versions.

Now close Synaptic, open a terminal, and enter:
```
wget -q http://lgp203.free.fr/public.key -O- | sudo apt-key add -
```
to get and add the gpg key.

Open Synaptic again, and press the "Reload" button; after that, you can find **codeblocks** there.

More information [here]("http://lgp203.free.fr/spip/spip.php?article2").

---

### Post by Pogeymanz on 2007-12-15
That does make my life a lot easier. Thanks!

Just for future knowledge, though, I'd like to figure what I'm doing wrong. I am really excited about Linux and want to learn as much as possible.

---

### Post by RomeReactor on 2007-12-15
Well, since code::blocks isn't a part of  regular Ubuntu repositories, doing **sudo apt-get build-dep codeblocks** wouldn't install the necessary dependencies for it. Most likely, the page where you downloaded the source would have instructions on how to install those dependencies, including **libtoolize**, or those instructions would come in the readme file.

---

