---
title: "Reset settings in beryl [quick]"
date: 2007-04-23
forum: Absolute Beginner Talk
---

### Post by the_axiom on 2007-04-23
Hi!
I need to reset the settings in beryl.
Anyone got any idea how to do? 

Thank you for your attention.

Regards
James

---

### Post by petersjm on 2007-04-23
What do you mean by "reset"? You can right-click on the Beryl "gem" icon on the taskbar and select "Beryl Manager" or whatever it's called (should be top of the list, if I'm not mistaken). From there, you can change the settings...

---

### Post by the_axiom on 2007-04-23
by reset I mean changing back all settings to default.
Siense i don't remember all the default settings, it would be quite hard...
I really need to fix this very soon because I need to record the beryl effects to a school project for tomorrow.

---

### Post by Waappu on 2007-04-23
> **the_axiom said:**
> by reset I mean changing back all settings to default.
Siense i don't remember all the default settings, it would be quite hard...
I really need to fix this very soon because I need to record the beryl effects to a school project for tomorrow.

Type in terminal
```
rm -r ~/beryl
rm ~/.beryl-managerrc
```
This will completly delete your old settings. Then reload window manager

---

### Post by the_axiom on 2007-04-24
> **Waappu said:**
> Type in terminal
```
rm -r ~/beryl
rm ~/.beryl-managerrc
```
This will completly delete your old settings. Then reload window manager
thank you for your answer!

The first command "rm -r ~/beryl" give me an error that says that there are no  such catalog...

---

### Post by Waappu on 2007-04-24
> **the_axiom said:**
> thank you for your answer!

The first command "rm -r ~/beryl" give me an error that says that there are no  such catalog...

Hi

Sorry about typo in code

try this```
rm -r /.beryl
```

---

### Post by the_axiom on 2007-04-25
That didn't work neither.
But i tried a combination of both of them and made it work:
rm -r ~/.beryl
rm ~/.beryl-managerrc

---

### Post by aquaeyed on 2007-04-25
do it mannual click on every brush in setings =) that only way that i know, sorry

---

### Post by Waappu on 2007-04-25
Hi

If you type in terminal ```
rm -r ~/.beryl
rm ~/.beryl-managerrc
```and then reload window manager it will reset all Beryl settings to defaults, but not change emerald theme

---

