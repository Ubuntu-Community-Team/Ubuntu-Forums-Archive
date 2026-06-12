---
title: "[SOLVED] Incorporating Ubuntu Into My Studies"
date: 2007-08-22
forum: Absolute Beginner Talk
---

### Post by tdrusk on 2007-08-22
I want two things...

1) A program that I can make flash card like things. Such as question, click, answer.
2) I have a lot of math notes that I would like to make more organized. I was considering typing them. I am in Calculus, so we use a lot of mathematical symbols. What would be the best program for this?

---

### Post by kidcharles on 2007-08-22
I don't know about the flash card thing, but there is a long-standing typesetting language called Tex (or LaTeX). It can be used to make just about any mathematical expression look just as you would write it (like differentiation and integration in calculus, for example). There are many (probably too many) latex editors out there, I don't know of any off hand, but at least you know how to start looking.

---

### Post by tdrusk on 2007-08-22
Any more suggestions?

---

### Post by Arthur Archnix on 2007-08-22
Well, the simplest way, the way that comes first to mind is to use open office. Create one document called questions, and one called answers.

For example, if question document you write:

Question 1:
What does 2+2 =
answer

Then in answer document you write:
Answer 1:
4

Then you create a hyperlink on the word answer and point it to a place in another document, Answer 1 in answers.odt

You may want to put the answers each on their own page so you don't see other answers.

You can create more complicated questions and answers using >insert >object >formula

---

### Post by Fonon on 2007-08-22
You can create flash cards in OO.o Presentation, and you can download OO.o math which you can use for math stuff.

---

### Post by Arthur Archnix on 2007-08-22
Fonon, that sounds interesting.

---

### Post by dwhitney67 on 2007-08-22
Unless you have phenomenal memory, the best way to learn things is to write them down using old-fashioned paper and pencil/pen.

If you spend too much time learning/mastering Open Office or LaTex, then you take away from the time you should be spending studying the subject at hand (in your case, Calculus).

Just my $0.02 worth of advice.

---

### Post by Arthur Archnix on 2007-08-22
> **dwhitney67 said:**
> Unless you have phenomenal memory, the best way to learn things is to write them down using old-fashioned paper and pencil/pen.

If you spend too much time learning/mastering Open Office or LaTex, then you take away from the time you should be spending studying the subject at hand (in your case, Calculus).

Just my $0.02 worth of advice.

Well, I read it and I want my $0.02 back. Let me take five minutes to set up two open-office documents and figure out what that will be in licorice candies from the corner store grandpa. :popcorn:

---

### Post by tdrusk on 2007-08-22
synaptic says I have Oo math installed, but it's not in my menu. All I have is database, presentation, spreadsheet, word processor. Is one of them math labeled differently?

---

### Post by jusmurph on 2007-08-22
> **fuzzyhair said:**
> synaptic says I have Oo math installed, but it's not in my menu. All I have is database, presentation, spreadsheet, word processor. Is one of them math labeled differently?

Have you installed the Debian Menu?

---

### Post by tdrusk on 2007-08-22
> **jusmurph said:**
> Have you installed the Debian Menu?

I have the default ubuntu menu.

---

### Post by jimrz on 2007-08-22
you might create a flash card type thing in OOo Base by setting up 2 tables "questions" & "answers", making a form for each displaying one item at a time, adding a "button" on the "questions" form which when clicked would open the "answers" form to the corresponding line, then a "close form" button on the "answers" form so you could then proceed to the next ? and repeat.

---

### Post by neoguy2012 on 2007-08-22
While in OO.o Impress, try Insert -> Object -> Formula.  I hope that helps!

Note: I use the pen and paper method myself when it comes time to memorize... but maybe this method works best for you.

---

### Post by wildkarde on 2007-08-22
If you want something web-based, I suggest quizlet.com
If you want something from the repos, you might want to try granule. 
If you want something else... you might want to try memorize-words.  
[http://memorize-words.sourceforge.net/](http://memorize-words.sourceforge.net/)  (java)

I haven't actually used them. Just thought that would help.

*EDIT*
Another option from the repos: memaid-pyqt.  (KDE based)

---

### Post by jusmurph on 2007-08-22
Debian Menu shows Everything that is installed, helpful with those things that don't show in the normal menu.

To get the Debian menu:

```
sudo apt-get install menu-xdg
sudo update-menus
```
restart X (ctrl + alt + backspace)

It then simply integrates with the main menu as a Category.

---

### Post by tdrusk on 2007-08-23
> **jusmurph said:**
> Debian Menu shows Everything that is installed, helpful with those things that don't show in the normal menu.

To get the Debian menu:

```
sudo apt-get install menu-xdg
sudo update-menus
```
restart X (ctrl + alt + backspace)tyler@tyler-laptop:~$ sudo update-menus
Password:
sudo: update-menus: command not found


It then simply integrates with the main menu as a Category.


any ideas?

---

### Post by jusmurph on 2007-08-29
> **fuzzyhair said:**
> any ideas?

A question with no content?

---

