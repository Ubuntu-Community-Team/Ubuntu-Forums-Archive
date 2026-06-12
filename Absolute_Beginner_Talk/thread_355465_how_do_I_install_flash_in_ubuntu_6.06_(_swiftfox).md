---
title: "how do I install flash in ubuntu 6.06 ( swiftfox)"
date: 2007-02-07
forum: Absolute Beginner Talk
---

### Post by basilwatson on 2007-02-07
Hi all having difficulty installing adobe flash 9 in swiftfox

basiclly no sound in youtube and some flash fail to open ( one assumes its flash 9 ) 

Have automatixs ,,use that ok ..  but when I went to  adobe site , downloaded flash 9 , followed instructions , i couldnt navigate to the swiftfox file 

tried $ cd swiftfox 
$/home/s/opt/swiftfox 

it keeps saying no file or directory ..

its there in . home ....s....opt...swiftfox..

What am I doing wrong??

Stephen

---

### Post by raul_ on 2007-02-07
/opt/ is not in your home dir. You should browse to /opt/swiftfox/plugins

next time do a 
```

locate swiftfox/plugins

```

;)

---

