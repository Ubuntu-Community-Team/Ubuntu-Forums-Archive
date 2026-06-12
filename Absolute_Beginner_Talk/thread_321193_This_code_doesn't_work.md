---
title: "This code doesn't work"
date: 2006-12-18
forum: Absolute Beginner Talk
---

### Post by linux-beginner on 2006-12-18
Hello

I want to run a streaming on a HTML file. The code I written, have also to run in a windows system. The code is:
```
<html>
<head>
<title>test</title>
</head>
<body>
<OBJECT id='mediaPlayer' width="320" height="285"
classid='CLSID:22d6f312-b0f6-11d0-94ab-0080c74c7e95' codebase='http://activex.microsoft.com/activex/controls/mplayer/en/nsmp2inf.cab#Version=5,1,52,701'
type='application/x-oleobject'>
<param name='test' value="test.ogg">
<param name='animationatStart' value='true'>
<param name='transparentatStart' value='true'>
<param name='autoStart' value="true">
<param name='showControls' value="true">
<param name='loop' value="true">
<EMBED type='application/x-mplayer2'
id='mediaPlayer' name='mediaPlayer' displaysize='4' autosize='-1'
bgcolor='darkblue' showcontrols="true" showtracker='-1'
showdisplay='0' showstatusbar='-1' videoborder3d='-1' width="320" height="285"
src="test.ogg" autostart="true" loop="true">
</EMBED>
</OBJECT>
</body>
</html>
```
But it doesn't work.
Could you guide me please?

Thanks,

---

### Post by hyper_ch on 2006-12-18
Well, I assume it won't work due to the activex as linux doesn't have that...

---

### Post by Pobega on 2006-12-18
I've never gotten Firefox to run those types of embedded videos, but you can always save them to your HDD and use MPlayer :)

---

