---
title: "firefox3Beta crashing when printing forum page"
date: 2008-03-24
forum: Absolute Beginner Talk
---

### Post by iansane on 2008-03-24
When I print a post from this forum to PDF or other printer, Firefox3Beta crashes at 75% sending print job. Error console shows "$ is not defined"  it's in the source of the pages but I don't know if that is causing the crash. No problem with main forum page or other sites. The line it highlights is ```
$('q').addEvent('focus', function() {

```

I'm now running firefox3 Beta on 8.04 AMD64 server with gnome and ubuntu-desktop installed so could be any number of things causing it. I filed abug report at bugzilla but wanted to let you guys know in case it is something in the code.

---

### Post by smartboyathome on 2008-03-25
This should be moved to the development section, since Hardy is not officially supported.

---

