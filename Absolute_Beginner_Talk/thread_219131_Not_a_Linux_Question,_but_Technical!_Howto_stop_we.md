---
title: "Not a Linux Question, but Technical! Howto stop website logging me out?"
date: 2006-07-19
forum: Absolute Beginner Talk
---

### Post by Thenotsowyzewun on 2006-07-19
Hi,

Is there a way I can change a website's cookie to remember me permanently, or at least until I close Firefox?
Businesslink.gov.uk seems to time out pretty quick (probably because the articles are long), and Firefox can't fill the login details 'cos of the way it's coded.

Thanks very much!

---

### Post by mattisking on 2006-07-19
The problem isn't really the website or your browser or your cookie. It has to do with something called the session. A browser session times out, generally, at 20 minutes. This is a standard controlled, in general, not by the way the website is written, but how the website is setup. For IIS (Windows) it could be overridden by the administrator of the site. For Linux using something like Apache, the same is true, but I don't know that tool. Ultimately, the browser "session" is a frustrating issue for web developers because it means you can't just leave something like a document sitting there and expect things to continue like normal when you pop up from your desk to go have lunch. Some newer web applications (web 2.0) might actually save your data to your account were you logged in and thus allow you to continue but not something like a relatively non-interactive web site. The only other way is to stay active. The session won't time out while you are actively browsing, but reading alone, without actually following a link doesn't count. It's frustrating, but it's the web. I'm sorry I can't offer you any better suggestions.

---

### Post by NT4usB on 2006-07-19
I don't know cookies but maybe the cookie is written to expire quickly?

There's a skript that will remember passwords for pages that are written to not allow passowrds to be remembered. I've never tried it.
[http://www.squarefree.com/bookmarklets/forms.html#remember_password]("http://www.squarefree.com/bookmarklets/forms.html#remember_password")
Might sign up at news.mozilla.org and look around there. Tons of useful info...

---

### Post by Thenotsowyzewun on 2006-07-19
Thanks for the replies, I'll ask on mozilla's site :)
Think you're right about it being session based tho (esp seeing as you're forum staff lol!)

---

### Post by jd65pl on 2006-07-19
Hi,

I work for a well known blue chip company with an internet job vacancy internet page, the session is terminated by the web server not client side so theres not much you can do, Not sure if all sites use this though.

---

