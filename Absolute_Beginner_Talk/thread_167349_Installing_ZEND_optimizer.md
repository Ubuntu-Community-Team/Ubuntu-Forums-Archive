---
title: "Installing ZEND optimizer ?"
date: 2006-04-28
forum: Absolute Beginner Talk
---

### Post by Blagomir on 2006-04-28
How can i install ZEND optimizer to my UBUNTU machine?

---

### Post by halfvolle melk on 2006-04-28
I don't know the first thing about php, but I found this:
```
jz@bc:~$ sudo apt-cache search zend
php4-apd - PHP code execution profiler and debugger
```

Synaptic has this to say about php4-apd:
> PHP code execution profiler and debugger
Advanced PHP Debugger is a full-featured PHP profiler/debugger that
is loaded as a zend_extension. It aims to be an analog of C's gprof
or Perl's Devel::DProf, and provides PHP developers with a number of
additional functions which can be used to obtain internal code
execution details such as timing information, function call tree and
stack backtrace. This is particularly useful for performance profiling
purposes. See pear.php.net/apd for more information.

If that's what you're looking for, you can install it like this:
```
sudo apt-get install php4-apd
```
or through Synaptic. It's in the universe repository.

---

### Post by songokuze on 2007-07-03
> **Blagomir said:**
> How can i install ZEND optimizer to my UBUNTU machine?

You can get Zend Optimizer for Linux on zend dot com and install it with XAMPP.

Regards,

---

