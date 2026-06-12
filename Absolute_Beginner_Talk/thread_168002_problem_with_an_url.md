---
title: "problem with an url"
date: 2006-04-29
forum: Absolute Beginner Talk
---

### Post by harys on 2006-04-29
hi, i have this error message when i try to open the link english live on [www.english-at-home.com](www.english-at-home.com) : "Sorry, this feature does not work with your browser." thanks for your reply. harys

---

### Post by mostwanted on 2006-04-29
I went to the site, clinked the link and looked at the source code. Apparently, the site uses proprietary Microsoft JScript to launch Windows Media Player

```
<script LANGUAGE="JavaScript">

function flashfile_DoFSCommand(command, args) 
{ 
if ( command == "filename" ) {document.mediaPlayer.fileName =args}
} 

</script>
```

which means their site will only work on Windows. Send them an email and say that they suck, there's not much else you can do. Sorry.

---

