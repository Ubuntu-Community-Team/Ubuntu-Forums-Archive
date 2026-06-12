---
title: "Evolution and Opera"
date: 2007-03-21
forum: Absolute Beginner Talk
---

### Post by Mr Green Genes on 2007-03-21
First post after nearly a year of silence!

I am currently using Evolution and Opera as my default applications.  When I click on a link in Evolution I can open Opera ok but only as a blank page, it never opens the link itself, however I set up system->preferences->preferred applications.

Has anyone got any clue about what I'm doing wrong?

---

### Post by zvacet on 2007-03-23
Why do you need Evolution when you have Opera?

---

### Post by joep-vd on 2007-08-11
> **zvacet said:**
> Why do you need Evolution when you have Opera?

Not a very constructive reply... I'm having a related problem: When I click a link in Evolution, Firefox starts up, even though the Preferred Application is Opera. And Kopete opens Konsole. Any clues how I could change the default webbrowser? 

And... When I click on an email address in Opera, it wants to start Opera Mail. To which file should I point Opera to open a new message in Evolution? 

Thank you very much.

---

### Post by Damiel on 2007-08-11
> **joep-vd said:**
> 
And... When I click on an email address in Opera, it wants to start Opera Mail. To which file should I point Opera to open a new message in Evolution? 


Go to Tools->Preferences->Advance->Programs and change the **mailto** protocol to: *evolution %s*

---

### Post by joep-vd on 2007-08-12
Thanks for your help... But it did not work out. Instead of loading Opera Mail, nothing happens after clicking a mailto. 

In my Konsole I get this: 

```
joep@mekanik:~$ evolution %s
CalDAV Eplugin starting up ...

(evolution-2.10:6256): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6256): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6256): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6256): DEBUG: mailto URL program: evolution

(evolution-2.10:6256): evolution-shell-WARNING **: Invalid URI: %s
```

But, after reading man evolution, I tried this: 

```
joep@mekanik:~$ evolution mailto:someone@example.org
CalDAV Eplugin starting up ...

(evolution-2.10:6286): evolution-mail-WARNING **: ignored this junk plugin: not enabled or we have already loaded one

(evolution-2.10:6286): e-utils-WARNING **: Plugin 'Bogofilter junk plugin' failed to load hook 'org.gnome.evolution.mail.junk:1.0'
** (evolution-2.10:6286): DEBUG: mailto URL command: evolution %s
** (evolution-2.10:6286): DEBUG: mailto URL program: evolution
(evolution-2.10:6286): e-data-server-DEBUG: Loading categories from "/home/joep/.evolution/categories.xml"
(evolution-2.10:6286): e-data-server-DEBUG: Loaded 29 categories
```

Which works as intended. And, curiously, contains the line evolution %s. 

Any ideas would be appreciated!

---

### Post by Damiel on 2007-08-13
> **joep-vd said:**
> Thanks for your help... But it did not work out. Instead of loading Opera Mail, nothing happens after clicking a mailto.
Sorry, I was wrong by one letter. Try this:
```
evolution %r
```

Got the command from [here]("http://www.opera.com/support/search/view/472/").

[QUOTE=Mr Green Genes]
I am currently using Evolution and Opera as my default applications. When I click on a link in Evolution I can open Opera ok but only as a blank page, it never opens the link itself, however I set up system->preferences->preferred applications.

Has anyone got any clue about what I'm doing wrong?
[/QUOTE]

Can you post the command in the Preferred Applications->Web Browser dialog? You should have something like this:
```

opera -newpage %s

```

---

### Post by stchman on 2007-08-13
> **zvacet said:**
> Why do you need Evolution when you have Opera?

I am not too familiar with Opera as I have never used it.

Isn't Opera a web browser and Evolution an email client?

---

### Post by zvacet on 2007-08-13
> Isn't Opera a web browser and Evolution an email client?

Opera is browser with integreted email cient.But,if somebody want to use it just for browsing this page may help
[https://help.ubuntu.com/community/OperaBrowser]("https://help.ubuntu.com/community/OperaBrowser")

Just select it for prefered bowser and don´t change anything for mail.I hope this will help you.

---

### Post by joep-vd on 2007-08-13
Thanks for helping me out, Damiel, this works! 

stchman, Opera is imho the finest browser. All the essential FF-plugins come installed, yet it is a lightweight browser. Especially recommended when working on an older machine, or working with a lot of tabs. Try it out! 

I'm not using the email client, since it isn't compatible with some required exchange options.

---

