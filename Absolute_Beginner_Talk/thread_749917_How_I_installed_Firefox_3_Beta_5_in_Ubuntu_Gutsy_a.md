---
title: "How I installed Firefox 3 Beta 5 in Ubuntu Gutsy and made my themes and extensions wo"
date: 2008-04-08
forum: Absolute Beginner Talk
---

### Post by rainserpent on 2008-04-08
Go to menu: system, software sources and click on the third-party software tab and then on add...

Add these repositories:
deb [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main & deb-src [http://ppa.launchpad.net/ubuntu-backporters/ubuntu](http://ppa.launchpad.net/ubuntu-backporters/ubuntu) gutsy main

Install in synaptic by searching in source for the repositories added.

Follow the Lifehacker blog The Complete Field Guide to Testing Firefox 3:[http://lifehacker.com/376551/the-complete-field-guide-to-testing-firefox-3](http://lifehacker.com/376551/the-complete-field-guide-to-testing-firefox-3) Basically, download the Nightly Tester Tools extension: [https://addons.mozilla.org/en-US/firefox/addon/6543]("https://addons.mozilla.org/en-US/firefox/addon/6543")
Once it's installed and you've restarted, your Firefox 3 Add-ons dialog will have a "Make all compatible" button, select that to make your extensions work with Firefox 3 (after a restart, that is).

Right click your link and select properties and browse to /usr/bin/firefox-3.0 to make the new Beta open. 2.0 is still installed and you can reopen it at any time.

This thread open to comments about this instillation procedure and how to make it better. As an additional note, I also backed up my Firefox profile before trying this.

---

### Post by GCoffee on 2008-04-14
haven't tested it out but that looks cool.

---

### Post by hyper_ch on 2008-04-14
wohoo... cool :) I miss a few extensions and haven't bothered to edit each one and change the versioning there :)

---

