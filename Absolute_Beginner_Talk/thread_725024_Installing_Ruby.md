---
title: "Installing Ruby"
date: 2008-03-15
forum: Absolute Beginner Talk
---

### Post by KTULU1 on 2008-03-15
I've installed Ruby on Gusty and the installation went well but it's nowhere to be fount, I've checked all the menus and found nothing. 
Am I missing something?

---

### Post by krendar on 2008-03-15
I am not sure if Ruby installs anything in the menus.

Try to open a command prompt (Applications|Accessories|Terminal) and type "ruby" and see if anything is written back like a version number.

---

### Post by jrib on 2008-03-15
You write your ruby script in your favorite text editor.  Then you have ruby parse that text file.

Here's a quick example:
[LIST=1]
[*]Step 1
Write your ruby script in your favorite text editor.
```
gedit helloworld.rb
```

Type in:
```
puts "hello world"
```
save and exit.

[*]Step 2
Tell ruby to parse your code.
```
ruby helloworld.rb
```
[/LIST]

That's a simple example.  Try going through the documentation at [http://www.ruby-lang.org/en/documentation/](http://www.ruby-lang.org/en/documentation/)

---

### Post by KTULU1 on 2008-03-15
:oops:

tnx! It works! :mrgreen:

---

### Post by hyperair on 2008-03-15
While you're at it you might like the Interactive Ruby prompt, irb. If you've used Ruby in Windows I'm sure you've seen it before. Install the "irb" package. Then start in the terminal, "irb". It'll give you a prompt.

---

