---
title: "Stability of Nvu"
date: 2007-04-20
forum: Absolute Beginner Talk
---

### Post by Neil Purling on 2007-04-20
I have installed Nvu to deal with editing saved ebay pages.
They are on the NTFS (hdb1) partition of my slave drive.
Right now I have opened and saved ablank page I use as a template. When I tried to scroll down the page Nvu disappeared. I had saved the page to a folder within my own folder on the Ubuntu side of this drive.
I tried to highlight some text to change the font and Nvu crashed again.
It doesnt seem to be an issue related to accessing the NTFS partition of hdb.

---

### Post by AAM on 2007-04-20
Suggestion: trying saving the file to the Ubuntu partition first and saving back after editing, all outside Nvu. This will establish whether Nvu is all to blame.

---

### Post by Neil Purling on 2007-04-20
As my post suggests I have already tried saving to the Ubuntu partition.
It is just as twitchy even on a page saved to my 'home' directory.
What i saved was a blank template of a simplified form of ebay page that I fill in with information. As soon as I clicked on a cell to get the cursor there it crashed, even before I typed anything. Even attempting to scroll down the page with the mouse wheel it crashes before I manage to enter any text.

---

### Post by compiledkernel on 2007-04-20
As I have always known, Nvu was abandoned by its developer. As such no updates are made to it, and It doesnt even appear on the Feisty repos as a standard package. 

sudo apt-get install amaya , might be a little better suited to your needs.

---

### Post by brian j on 2007-04-20
QuestionIs the Nvu project still active?
    AnswerYes! Daniel Glazman is currently leading development on the next generation HTML editor. It is being completely redone to take advantage of new features in the Firefox development branch. For more information please visit our forums.

---

### Post by Neil Purling on 2007-04-20
Where does amaya hide itself after one has installed the package?

---

