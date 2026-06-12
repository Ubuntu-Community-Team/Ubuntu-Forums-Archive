---
title: "Epiphany rendering using GTK or gecko using GTK?"
date: 2006-12-28
forum: Absolute Beginner Talk
---

### Post by Ben Sprinkle on 2006-12-28
Anyone know of a way to make Epiphany render the widgets and dialogs using GTK and not the ugly default gecko engine?
Or letting gecko render using the GTK?

---

### Post by Perfect Storm on 2006-12-28
:confused: 

Epiphany browser are using GTK2 in every way, or am I misunderstanding the question?

---

### Post by Ben Sprinkle on 2006-12-28
> **Artificial Intelligence said:**
> :confused: 

Epiphany browser are using GTK2 in every way, or am I misunderstanding the question?

Like the buttons and widgets. They are not being rendered using my GTK theme, or my engine for that matter.
Hmm?

---

### Post by Perfect Storm on 2006-12-28
hmmm..seems something is wrong with your epiphany then, I don't what.



Here's how mine epiphany looks like, everything with GTK2 and icons etc.

Which version of Ubuntu do you use? Have you tried changing GTK2 themes to see if the theme isn't broken?

---

### Post by Ben Sprinkle on 2006-12-28
Screen your google.com, I use my own OS with ubuntulooks engine.

---

### Post by Perfect Storm on 2006-12-28
Ah, I see.
Never bothered me, I'll see if I can find some info on it.

---

### Post by mcduck on 2006-12-28
It seems to me that Epiphany uses same widgets that Firefox uses, as I have configured prettier widgets for FF and Epiphany is now using them too..

edit: [Screenshot]("http://www.elisanet.fi/pontus.schonberg/random/epiphany.jpg")

---

### Post by Perfect Storm on 2006-12-28
Perhaps compile the gecko engine an then compiling epiphany with prefixing to the compiled gecko engine: [http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites](http://developer.mozilla.org/en/docs/Linux_Build_Prerequisites) then you have the option to enable/disable stuff. If the ubuntu devs decided to have gecko/epiphany in one way, this is an option to follow.

Gonna try this when I get home from work and see if it fix the problem.

---

### Post by Ben Sprinkle on 2006-12-28
Mcduck, how did you get your buttons to use a different engine? Mine use the Redmond or some really generic ulgy engine.

---

### Post by mcduck on 2006-12-29
It's not actually using any theme, just the widget images I have installed for Firefox. Looks a lot nicer than default ones, anyway ;)

It seems like the following trick also changes the widgets in Epiphany:```
wget http://koti.mbnet.fi/~ots/artwork/firefox-form-widgets-ots.tar.gz
tar -xvzf firefox-form-widgets-ots.tar.gz

sudo cp /usr/lib/mozilla-firefox/res/forms.css /usr/lib/mozilla-firefox/res/forms.css.bak
cat firefox-form-widgets-ots/res/forms-extra.css | sudo tee --append /usr/lib/mozilla-firefox/res/forms.css > /dev/null
sudo cp -r firefox-form-widgets-ots/res/form-widgets /usr/lib/mozilla-firefox/res

rm -rf firefox-form-widgets-ots

```

edit: it seems that the link is not working any more, I'll just attach the package to this message then :)

---

### Post by Ben Sprinkle on 2006-12-29
I'll go test later.

---

