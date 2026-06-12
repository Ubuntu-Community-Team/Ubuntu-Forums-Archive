---
title: "kubuntu feisty: setting default applications"
date: 2007-04-21
forum: Absolute Beginner Talk
---

### Post by Ba66e77 on 2007-04-21
I have my default browser set to firefox in the System Settings -> Default Applications area.  Nonetheless, when I click on a web link in any app other than Firefox, the link opens in Konquerer.

I'm having a similar problem with using Thunderbird as my default email app.  Before I uninstalled kmail (or whatever), mail links opened in kmail, since I uninstalled it nothing happens.

It's not a huge deal, but it's a persistent annoyance that's starting to make me nuts.  Is there some trick I'm missing that will make this work?

---

### Post by Obor on 2007-04-21
This should let you choose default browser. Worked fine on my Kubuntu Feisty
```
sudo update-alternatives --config x-www-browser
```

Edit: My mailto: links open iin thunderbird but i can't remember what I've done to make it work.

---

### Post by Ba66e77 on 2007-04-21
Excellent!  Worked like a charm.  Many thanks.

---

