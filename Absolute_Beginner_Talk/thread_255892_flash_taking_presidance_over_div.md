---
title: "flash taking presidance over div"
date: 2006-09-12
forum: Absolute Beginner Talk
---

### Post by satish_maurya@rediffmail. on 2006-09-12
I have a problem with LINUX OS where Flash is taking precedance over a DIV menu.
I have declared a flash on index page.over this flash top menu DIV is not coming properly.Flash is hiding my Top Menu DIV.
I have set z index , presedance also.but it doesn't 
worked.please suggest me solution ...

---

### Post by Japh on 2008-03-13
I haven't found a way to fix that in Linux but I do know of a fix for windos machines.

Here is what worked for me in windows:

    Specify the below <param> tag in your <object> tag:
          <param name="wmode" value="transparent">

     Then give the <embed> tag an attribute like this:
         wmode="transparent"
      Example:
         <embed src="flash.swf" wmode="transparent">
---
Example:
<object>
<param name="wmode" value="transparent">
<embed src="flash.swf" wmode="transparent">
</object>

That's what worked for my pages in windows, but I haven't found a way to fix it in my linux.

Actually I just now tested the fix on the mac machine here at work and it worked. So it seems linux is the one that's not working :-/.

This fix works for(as far as I've tested):

Windows: Firefox, Safari, Opera, IE
Mac: Safari, Opera

--J

---

