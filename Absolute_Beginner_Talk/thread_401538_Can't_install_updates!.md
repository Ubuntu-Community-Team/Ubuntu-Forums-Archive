---
title: "Can't install updates!"
date: 2007-04-04
forum: Absolute Beginner Talk
---

### Post by ciarals on 2007-04-04
Hi!
I'm new here. I'm so impressed of ubuntu and I really love it. I have set up everything (wireless, settings, etc...) but for some reason updates don't work. There are 181 updates ready to download and install: I click on the Install button, he checks the updates and then everything stops and my updates are still there. Why? What can I do? Thank you very much for help.

---

### Post by brentoboy on 2007-04-04
I'm not sure what the root problem here is, but maybe it will be fixed by one of those updates, so here is a temporary fix (which will  install all the latest updates without using that update icon)

open a terminal (Applications > Accessories > Terminal)
and type this:

```

sudo apt-get update
sudo apt-get upgrade

```

after typing the first line, it will get a list of the latest things.
The second line will download and install all of them.
(if it asks questions, say "yes")

if the icon doesnt become "happy" after that, log out and log back in, that should restart the program that manages that little icon.

---

### Post by ciarals on 2007-04-04
Thanks for the answer. While I was waiting for some answer, I was looking the forum and I read a user that was having a problem like mine. The answer was similar to yours, except for the second line: infact in his answer the second line was like this: 

sudo apt-get dist-upgrade

That "dist" makes any difference? What is better for me to do? And why the software update utility doesen't work? Thanks a lot. Bye bye!

---

### Post by brentoboy on 2007-04-04
the dist part means you intend to jump from one version to another with as little hassel as possible.

for instance, you might want to go from dapper to edgy.  So, you change your repos to edgy update and do a dist-upgrade.

without the dist, it wont add new packages it will only update existing ones, and add any new ones that are needed to support newer versions of what you have.

dist upgrade means "add the new stuff that has been added for the new version of ubutnu"

now, in your current situation, it wont be any different, because your repos still  point to whatever version you already have installed.  So, if you are running edgy, and you say dist-upgrade it will upgrade you to edgy -- big whoop.  So, I guess deep down, they are more or less equivalent.

---

### Post by ciarals on 2007-04-04
Ok, thanks for the help! It was very useful for me!

---

