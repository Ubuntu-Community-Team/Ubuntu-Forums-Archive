---
title: "echo'ing highlighted text"
date: 2006-05-13
forum: Absolute Beginner Talk
---

### Post by tux101 on 2006-05-13
How do I echo highlighted text?

---

### Post by Kvark on 2006-05-13
Err, do you mean give the text you have selected to the terminal command "echo"? :?

Middle click pastes the text that you have selected/marked/highlighted. So select some text. Go to a terminal window and type "echo ". Then middle click in the terminal window and hit enter.

---

### Post by tux101 on 2006-05-13
No, I mean what I said in the first place.

How do I echo text with highlights.  Assuming the you have the original white text black background look in terminal.  How would I echo something and have it in black text and white background?

---

### Post by Kvark on 2006-05-13
Oh... of couse, stupid me I should have understood that.

This is how:
```
echo -e "\E[7mthis is highlighted with reverse video\E[0m"
```

Look here for the other ansi escape codes:
[http://en.wikipedia.org/wiki/ANSI_escape_code](http://en.wikipedia.org/wiki/ANSI_escape_code)

---

### Post by tux101 on 2006-05-13
Thanks plenty!

---

