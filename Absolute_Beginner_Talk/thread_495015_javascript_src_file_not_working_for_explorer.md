---
title: "javascript src file not working for explorer"
date: 2007-07-07
forum: Absolute Beginner Talk
---

### Post by prostock3 on 2007-07-07
Hi,:KS

i'm just starting my first program in javascript. i use ubuntu feisty fawn. For some reason, I try to source the *.js file, the js only works on firefox. When I try explorer, it does not work. If I code the alert directly into the *.html file, it works fine. Anyone have any ideas?

Thanks! I posted the code below.

Inside /var/www/apache2-default , I have two files which i created (example.js, test.html)

test.html:

<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.1//EN"
"http://www.w3.org/TR/xhtml11/DTD/xhtml11.dtd">
<html xmlns="http://www.w3.org/1999/xhtml11" xml:lang="en">
<head>
<meta http-equiv="content-type" content="text/html; charset=utf-8" />
<title>Just a test</title>
<script type="text/javascript" src="example.js" >
alert(234);
</script>
</head>
<body>
</body>
</html>

example.js
alert(20);

---

