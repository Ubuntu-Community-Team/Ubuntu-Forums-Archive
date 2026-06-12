---
title: "App that downloads everything from a remote dir"
date: 2005-11-15
forum: Absolute Beginner Talk
---

### Post by Diod on 2005-11-15
Hey i need an app that downloads every file from a remote dir(from like a website). I need this because i want to skip the download limit of a site(not the speed limit, but the limit of files a day, u may only dl about 3 files a day on the site, while there are 30 files i need).
Thank you.

---

### Post by davmac on 2005-11-15
I'm not sure about gui based tools to do this but if you're comfortable with the command line, have a go at using wget.

A command like "wget -r -c http://www.thenameofthewebsite.com/" should do the trick. It'll create a directory called [www.nameofthewebsite.com](www.nameofthewebsite.com) and plonk everything it finds in there.

The -r option recurses down through the directory structure and the -c option will pick up where you left off if it gets interrupted for any reason.

I've only ever used this on webpages with static content. As soon as you start trying to grab dynamically built data (such as PHP or ASP) stuff, I think you may run into problems.

Hope this helps,

Dave Mac

---

### Post by Diod on 2005-11-16
Worked great, thanks!

---

