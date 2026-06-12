---
title: "problem with python"
date: 2008-02-09
forum: Absolute Beginner Talk
---

### Post by stunningman on 2008-02-09
i am learning python,but whenever i try to make a new function it do not run or there is an error
what i did:
def newLine()
print"First Line."
newLine()
print"Second Line."

now what to do next i am stuck up here.
can any body help me.
as i am totally new to programming.

---

### Post by codeslicer on 2008-02-09
Try a python tutorial? python.org seems good. I don't program in Python, so I don't know if there is something wrong in your syntax. However, make sure you have the python2.5-dev and python2.5-dbg packages installed. Those packages are used for development, and can be installed by using the Synaptic Package Manager found in System->Administration. Enjoy :guitar:

---

### Post by emarkd on 2008-02-09
First, Python is very sensitive to spaces.  Make sure you're putting four spaces (not tabs) for your indents.

Second, you have to put a colon after that def statement.  So it's like this:

```

def newLine():
    print "First Line"
newLine()
print "Second Line"

```

I didn't test that, but it should work.

---

### Post by emarkd on 2008-02-09
By the way, the default Ubuntu text editor, gedit, makes a fine python editor.  Just click on Edit > Preferences, select the Editor tab and teill it to uses 4 spaces instead of a tab.  Now you can hit tab like you're used to and it'll automatically insert 4 spaces instead of the tab character.

---

