---
title: "position:relative; to a negatively positioned div?"
date: 2011-07-16
forum: Art &amp; Design
---

### Post by maclenin on 2011-07-16
Essentially, I am trying to place 5 items next to one another - all at a position of **top:-20px;** and **left:10px;** of the previous item.

#item1 {position:absolute; top:-20px; left:10px;}
#item2 {position:relative; top:0px; left:10px;}
#item3 {position:relative; top:0px; left:20px;}
#item4 {position:relative; top:0px; left:30px;}
#item5 {position:relative; top:0px; left:40px;}

The resulting layout is something similar to:
```
item1
          item2
                    item3
                              item4
                                        item5
```
Any suggestions on how to enjoy...
```
item1    item2    item3    item4    item5
```
...relatively?

Thanks for any guidance!

---

### Post by DependencyHell on 2011-07-17
Hm...could you use the  negative size of item 1 instead the 0 px for top?

---

### Post by DependencyHell on 2011-07-17
Or put "bottom"  instead of top? :) Trying to guess...

---

### Post by Isaacgallegos on 2011-07-17
One thing that can matter is your header: 

<!DOCTYPE HTML> 

put that at the very top of your html document. It might help with css problems.


For divs next to each other, make them use 

float:left;

or 

float:right;

while being 

position: relative;

---

### Post by madebyjordan on 2011-07-18
Yep, as Isaacgallegos mentioned, why not just float the items? Use a negative top margin, eg margin-top:-20px; to achieve the effect you want.

---

### Post by maclenin on 2011-07-20
Thanks, all, for your replies and suggestions.... After further review and trials and errors, your solution, **Isaacgallegos** turned out to be the winning one...

```

#item1,
#item2,
#item3,
#item4,
#item5,
#item6 {position:relative; top:-20px; float:left; margin:10px;}
```

...with the items' order in the html (1,2,3... vs. 6,5,4...) determining their ultimate order in the browser....

Thanks for the guidance!

---

### Post by Isaacgallegos on 2011-07-20
Cool. If it dosen't work across different browsers, you might need to paste <!DOCTYPE HTML> at the very top or a different doctype.

---

### Post by maclenin on 2011-07-23
Yep - doctype is:

```
<!DOCTYPE html PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN" "http://www.w3.org/TR/html4/loose.dtd">
```

Thanks, again, for the comments!

---

