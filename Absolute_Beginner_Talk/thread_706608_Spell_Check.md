---
title: "Spell Check?"
date: 2008-02-24
forum: Absolute Beginner Talk
---

### Post by fetisha on 2008-02-24
This is a little weird. I'm a horrible speller, and I've noticed that in openoffice, firefox and AbiWord, the spell check is enabled, but it doesn't work (I write words wrong on purpose and it doesn't pick it up in any of the programs I mentioned). Do I need to do something in the settings or...?

---

### Post by seventhc on 2008-02-24
If your in Open Office, at the top there is a button that says *AutoSpellCheck*
is that clicked in yours?
It works in mine, and I don't remembering doing anything special, so thats all I can think of off the top of my head.
Check that first. :)

---

### Post by fetisha on 2008-02-24
> **seventhc said:**
> If your in Open Office, at the top there is a button that says *AutoSpellCheck*
is that clicked in yours?
It works in mine, and I don't remembering doing anything special, so thats all I can think of off the top of my head.
Check that first. :)

Yeah, it's clicked and still nothing.

---

### Post by Kingsley on 2008-02-24
Make sure you have myspell installed. I think the package is called myspell-en-us in Ubuntu.

---

### Post by seventhc on 2008-02-24
Thats weird, I can't remember installing any dictionaries or anything...if I did, I don'y know why I would since I rarely use open office. :confused:
I'd be more likely to install a spell check plugin into vim first.
There are a lot of people who are using open office though, so they will probably be able to help more. If I find info on it, I'll post back here.

---

### Post by asmoore82 on 2008-02-24
> **fetisha said:**
> This is a little weird. I'm a horrible speller, and I've noticed that in openoffice, firefox and AbiWord, the spell check is enabled, but it doesn't work (I write words wrong on purpose and it doesn't pick it up in any of the programs I mentioned). Do I need to do something in the settings or...?

the issue for Firefox, is that it is very difficult for it to tell the difference between boxes that should be SpellCheck'ed
and those that shouldn't(usernames, passwords, addresses, etc).

To make Firefox simply spell check everything:
1. in the url "address" bar, type ```
about:config
```
2. in the "Filter:" field at the top, type "spellcheck"
3. double-click on the "layout.spellcheckDefault" integer key where:
"0" means spell check off, "1" means spell check on, and "2" means spell check everything,
an option which cannot be set through the normal GUI Preferences, so
4. set this key to "2" and click "OK" (this is the default for the Camino Web Browser[Mac firefox])
5. you're done, close "about:config"

---

### Post by fetisha on 2008-02-24
> **asmoore82 said:**
> the issue for Firefox, is that it is very difficult for it to tell the difference between boxes that should be SpellCheck'ed
and those that shouldn't(usernames, passwords, addresses, etc).

To make Firefox simply spell check everything:
1. in the url "address" bar, type ```
about:config
```
2. in the "Filter:" field at the top, type "spellcheck"
3. double-click on the "layout.spellcheckDefault" integer key where:
"0" means spell check off, "1" means spell check on, and "2" means spell check everything,
an option which cannot be set through the normal GUI Preferences, so
4. set this key to "2" and click "OK" (this is the default for the Camino Web Browser[Mac firefox])
5. you're done, close "about:config"

Done, but it's still letting me spell words wrong on firefox :(

---

### Post by fetisha on 2008-02-24
> **Kingsley said:**
> Make sure you have myspell installed. I think the package is called myspell-en-us in Ubuntu.

Where would I find this? How would I install?

---

### Post by Duck2006 on 2008-02-24
> **fetisha said:**
> Where would I find this? How would I install?

Have you looked in your Synaptic Package Manager?

---

### Post by steve-shinn on 2008-02-24
Synaptic package manager

---

### Post by asmoore82 on 2008-02-24
> **fetisha said:**
> Done, but it's still letting me spell words wrong on firefox :(
you probably have to close and open firefox for the change to take effect.

---

### Post by mivo on 2008-02-24
Just to isolate the problem a little, please open a terminal window and type:

```
whereis myspell
whereis aspell
```

How does the system respond?

---

### Post by fetisha on 2008-02-24
Thank you all! It works just great now, on openoffice and firefox.

---

