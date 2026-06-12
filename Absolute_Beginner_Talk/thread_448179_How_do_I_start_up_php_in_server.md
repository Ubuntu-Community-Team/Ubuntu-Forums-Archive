---
title: "How do I start up php in server?"
date: 2007-05-18
forum: Absolute Beginner Talk
---

### Post by Cheese Sandwich on 2007-05-18
I'm running ubuntu server with LAMP, and have added my first php statement in the website I'm building. However, when I access the website from outside, the php code isn't getting executed. When I do:

ps aux | grep php

all that's shown is the "grep php" call.

How do I get php started up? Btw I typed "php" on the command line, & it told me to:

sudo apt-get install php5-cli

which I did, but no dice...

-Thx

---

### Post by Cheese Sandwich on 2007-05-18
Never mind - I just realized that the html file has to end in ".php"... But then how do you do php in index.html??

---

### Post by Cheese Sandwich on 2007-05-18
I guess an instant redirect would do the trick:

<html>
<head>
<link rel="stylesheet" href="style.css">
<META HTTP-EQUIV="Refresh"
      CONTENT="0; URL=index.php"></head>
<body>

</body>
</html>

---

