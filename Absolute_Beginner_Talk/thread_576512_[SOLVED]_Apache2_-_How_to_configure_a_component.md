---
title: "[SOLVED] Apache2 - How to configure a component?"
date: 2007-10-15
forum: Absolute Beginner Talk
---

### Post by vortex0007 on 2007-10-15
I'm just beginning to learn Apache2 and have what I hope is a simple question about getting it configured properly on Ubuntu 7.04.

Here's what's happening: 

I open  [www.mywebsite.com](www.mywebsite.com) - I get a blank page

I open [www.mywebsite.com/subfolder1/main.php](www.mywebsite.com/subfolder1/main.php) - everything loads correctly and works great.

What do I need to do to make [www.mywebsite.com](www.mywebsite.com) load the content found at [www.mywebsite.com/subfolder1/main.php](www.mywebsite.com/subfolder1/main.php) instead of a blank page?

Thanks.

NEVERMIND - I FOUND THE ANSWER. I had correctly edited my DocumentRoot path but it wasn't working because I didn't restart the service. Once I restarted the service using "apache2 restart" things work great.

---

