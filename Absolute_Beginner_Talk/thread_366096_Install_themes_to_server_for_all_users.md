---
title: "Install themes to server for all users"
date: 2007-02-20
forum: Absolute Beginner Talk
---

### Post by twtmc on 2007-02-20
Ok, here is the deal. My school has an ubuntu computer lab, and all of our accounts are stored on a server and we access them from 30 seperate computers. The computer teacher would like new themes on all the accounts, but doesn't know how, and frankly, neither do I. I already have the themes selected and downloaded, how do I automatically install them to all the user's accounts? (I have root access as well)

---

### Post by K.Mandla on 2007-02-20
I don't know how that works, but the first thing I can think of is to decompress the theme to /usr/share/themes/ on the server. My logic is that the default themes are usually stored there (with some exceptions), so perhaps including your themes in that location would include them in the list of options for all the users.

But again, I've never worked with that kind of setup, so that might be so completely wrong as to be embarrassing. :oops:

---

### Post by mcduck on 2007-02-20
That's right, put the themes in /usr/share/themes and icons in /usr/share/icons, and then they will be available for all users.

If you also want to force some theme to all users,take a look at Sabayon Profile Editor: [http://www.gnome.org/~seth/blog/sabayon]("http://www.gnome.org/~seth/blog/sabayon")

---

