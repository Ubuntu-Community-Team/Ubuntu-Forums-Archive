---
title: "Error while starting Swiftfox / Firefox (Feisty Fawn"
date: 2007-07-04
forum: Absolute Beginner Talk
---

### Post by Liakath on 2007-07-04
Dear all,

Recently I have started getting an error (Screenshot is attached) whenever I start FireFox / Swiftfox (latest version 2.0.0.4 from repos). It disappears when I press OK and after that both the browsers work normally. Any clue what it is about? How to get rid of the same? Otherwise there is no problem with the browsers

I am running Feisty Fawn with dual boot Win XP Pro with all the latest updates. My system specs are in my signature. I have been using Ubuntu since the new release.

---

### Post by Moop on 2007-07-04
It's probably one of your extensions causing the error. You can create a new profile and use that and see if you get the error. Then add your extensions one at a time to find out which one is causing the problem. It's a lot of work if you have a large number of extensions. 
Creating a new profile won't delete your old one and you can go back anytime. 
```
firefox -profilemanager
```

---

### Post by Liakath on 2007-07-04
> **Moop said:**
> It's probably one of your extensions causing the error. You can create a new profile and use that and see if you get the error. Then add your extensions one at a time to find out which one is causing the problem. It's a lot of work if you have a large number of extensions. 
Creating a new profile won't delete your old one and you can go back anytime. 
```
firefox -profilemanager
```

I have uninstalled all the extensions. The error message disappeared. I will reinstall one by one and hopefully find the offending one. Thanks for the response.

I found that after installing "Forecastfox 0.9.5.2" from Mozilla Extensions the Error Message reappears in Swiftfox. But I have been earlier having this extension without any error message. It is rather strange. Even older "Forecastfox 0.9.5" throws up the same error now. May be I have to live without it.

[COLOR="Red"]**The thread may be closed**[/COLOR]

---

