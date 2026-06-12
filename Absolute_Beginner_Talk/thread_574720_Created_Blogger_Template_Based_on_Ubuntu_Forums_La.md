---
title: "Created: Blogger Template Based on Ubuntu Forums Layout"
date: 2007-10-13
forum: Absolute Beginner Talk
---

### Post by justinmiller87 on 2007-10-13
I hope this is an appropriate place to post this; if not, the Powers That Be can move it. I created a Blogger template based on Minima to simulate the look of the Ubuntu Forums. I am also sharing it with anyone who wants to use it, so the code will follow. If you want to see what it looks like, you can view it here: [Welcome To Ubuntu](http://welcometoubuntu.blogspot.com)

```
<?xml version="1.0" encoding="UTF-8" ?>
<!DOCTYPE html PUBLIC "-//W3C//DTD XHTML 1.0 Strict//EN" "http://www.w3.org/TR/xhtml1/DTD/xhtml1-strict.dtd">
<html expr:dir='data:blog.languageDirection' xmlns='http://www.w3.org/1999/xhtml' xmlns:b='http://www.google.com/2005/gml/b' xmlns:data='http://www.google.com/2005/gml/data' xmlns:expr='http://www.google.com/2005/gml/expr'>
  <head>
    <b:include data='blog' name='all-head-content'/>
    <title><data:blog.pageTitle/></title>
    <b:skin><![CDATA[/*
-----------------------------------------------
Blogger Template Style
Name:     Ubuntu Forums Style
Designer: Justin Miller
URL:      http://welcometoubuntu.blogspot.com
Date:     12 Oct 2007
----------------------------------------------- */

/* Variable definitions
   ====================
   <Variable name="bgcolor" description="Page Background Color"
             type="color" default="#d3caaa" value="#d3caaa">			 
   <Variable name="textcolor" description="Text Color"
             type="color" default="#333" value="#333333">
   <Variable name="linkcolor" description="Link Color"
             type="color" default="#58a" value="#5588aa">
   <Variable name="pagetitlecolor" description="Blog Title Color"
             type="color" default="#666" value="#666666">
   <Variable name="descriptioncolor" description="Blog Description Color"
             type="color" default="#999" value="#999999">
   <Variable name="titlecolor" description="Post Title Color"
             type="color" default="#c60" value="#cc6600">
   <Variable name="bordercolor" description="Border Color"
             type="color" default="#ccc" value="#cccccc">
   <Variable name="sidebarcolor" description="Sidebar Title Color"
             type="color" default="#999" value="#999999">
   <Variable name="sidebartextcolor" description="Sidebar Text Color"
             type="color" default="#666" value="#666666">
   <Variable name="visitedlinkcolor" description="Visited Link Color"
             type="color" default="#999" value="#999999">
   <Variable name="bodyfont" description="Text Font"
             type="font" default="normal normal 100% Georgia, Serif" value="normal normal 100% Georgia, Serif">
   <Variable name="headerfont" description="Sidebar Title Font"
             type="font"
             default="normal normal 78% ,'Trebuchet MS',Trebuchet,Arial,Verdana,Sans-serif" value="normal normal 78% ,'Trebuchet MS',Trebuchet,Arial,Verdana,Sans-serif">
   <Variable name="pagetitlefont" description="Blog Title Font"
             type="font"
             default="normal normal 200% Georgia, Serif" value="normal normal 200% Georgia, Serif">
   <Variable name="descriptionfont" description="Blog Description Font"
             type="font"
             default="normal normal 78% 'Trebuchet MS', Trebuchet, Arial, Verdana, Sans-serif" value="normal normal 78% 'Trebuchet MS', Trebuchet, Arial, Verdana, Sans-serif">
   <Variable name="postfooterfont" description="Post Footer Font"
             type="font"
             default="normal normal 78% 'Trebuchet MS', Trebuchet, Arial, Verdana, Sans-serif" value="normal normal 78% 'Trebuchet MS', Trebuchet, Arial, Verdana, Sans-serif">
*/

/* Use this with templates/template-twocol.html */

body {
  background:$bgcolor url(http://ubuntuforums.org/imagesorig/ub2/bgrepeat.jpg) repeat-x;
  margin:0;
  color:$textcolor;
  font:x-small Georgia Serif;
  font-size/* */:/**/small;
  font-size: /**/small;
  text-align: center;
  }
a:link {
  color:$linkcolor;
  text-decoration:none;
  }
a:visited {
  color:$visitedlinkcolor;
  text-decoration:underline;
  }
a:hover {
  color:$titlecolor;
  text-decoration:underline;
}
a img {
  border-width:0;
  }

/* Header
-----------------------------------------------
 */

#header-wrapper {
  width:660px;
  margin:0 auto 10px;
  border:1px solid $bordercolor;
  background: #ffffff;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
  }

#header-inner {
  background-position: center;
  margin-left: auto;
  margin-right: auto;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
}

#header { 
  margin: 5px;
  border: 1px solid $bordercolor;
  text-align: center;
  color:$pagetitlecolor;
}

#header h1 {
  margin:5px 5px 0;
  padding:15px 20px .25em;
  line-height:1.2em;
  text-transform:uppercase;
  letter-spacing:.2em;
  font: $pagetitlefont;
}

#header a {
  color:$pagetitlecolor;
  text-decoration:none;
  }

#header a:hover {
  color:$pagetitlecolor;
  }

#header .description {
  margin:0 5px 5px;
  padding:0 20px 15px;
  max-width:700px;
  text-transform:uppercase;
  letter-spacing:.2em;
  line-height: 1.4em;
  font: $descriptionfont;
  color: $descriptioncolor;
 }

#header img {
  margin-left: auto;
  margin-right: auto;
}


/* Outer-Wrapper
----------------------------------------------- */
#outer-wrapper {
  width: 780px;
  margin:0 auto;
  padding:10px;
  text-align:left;
  font: $bodyfont;
  }

#main-wrapper {
  width: 518px;
  float: left;
  background: #ffffff;
  padding-left:10px;
  padding-right:10px;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
  word-wrap: break-word; /* fix for long text breaking sidebar float in IE */
  overflow: hidden;     /* fix for long non-text content breaking IE sidebar float */
  }

#sidebar-wrapper {
  width: 225px;
  float: right;
  padding:5px;
  -moz-border-radius: 10px;
  -webkit-border-radius: 10px;
  background: #ffffff;
  word-wrap: break-word; /* fix for long text breaking sidebar float in IE */
  overflow: hidden;      /* fix for long non-text content breaking IE sidebar float */
}



/* Headings
----------------------------------------------- */

h2 {
  margin:1.5em 0 .75em;
  font:$headerfont;
  line-height: 1.4em;
  text-transform:uppercase;
  letter-spacing:.2em;
  color:$sidebarcolor;
}


/* Posts
-----------------------------------------------
 */
h2.date-header {
  margin:1.5em 0 .5em;
  }

.post {
  margin:.5em 0 1.5em;
  border-bottom:1px dotted $bordercolor;
  padding-bottom:1.5em;
  }
.post h3 {
  margin:.25em 0 0;
  padding:0 0 4px;
  font-size:140%;
  font-weight:normal;
  line-height:1.4em;
  color:$titlecolor;
}

.post h3 a, .post h3 a:visited, .post h3 strong {
  display:block;
  text-decoration:none;
  color:$titlecolor;
  font-weight:normal;
}

.post h3 strong, .post h3 a:hover {
  color:$textcolor;
}

.post p {
  margin:0 0 .75em;
  line-height:1.6em;
}

.post-footer {
  margin: .75em 0;
  color:$sidebarcolor;
  text-transform:uppercase;
  letter-spacing:.1em;
  font: $postfooterfont;
  line-height: 1.4em;
}

.comment-link {
  margin-left:.6em;
  }
.post img {
  padding:4px;
  border:1px solid $bordercolor;
  }
.post blockquote {
  margin:1em 20px;
  }
.post blockquote p {
  margin:.75em 0;
  }

/* Comments
----------------------------------------------- */
#comments h4 {
  margin:1em 0;
  font-weight: bold;
  line-height: 1.4em;
  text-transform:uppercase;
  letter-spacing:.2em;
  color: $sidebarcolor;
  }

#comments-block {
  margin:1em 0 1.5em;
  line-height:1.6em;
  }
#comments-block .comment-author {
  margin:.5em 0;
  }
#comments-block .comment-body {
  margin:.25em 0 0;
  }
#comments-block .comment-footer {
  margin:-.25em 0 2em;
  line-height: 1.4em;
  text-transform:uppercase;
  letter-spacing:.1em;
  }
#comments-block .comment-body p {
  margin:0 0 .75em;
  }
.deleted-comment {
  font-style:italic;
  color:gray;
  }

#blog-pager-newer-link {
  float: left;
 }
 
#blog-pager-older-link {
  float: right;
 }

#blog-pager { 
  text-align: center;
 }

.feed-links {
  clear: both;
  line-height: 2.5em;
}

/* Sidebar Content
----------------------------------------------- */
.sidebar { 
  color: $sidebartextcolor;
  line-height: 1.5em;
 }

.sidebar ul {
  list-style:none;
  margin:0 0 0;
  padding:0 0 0;
}
.sidebar li {
  margin:0;
  padding:0 0 .25em 15px;
  text-indent:-15px;
  line-height:1.5em;
  }

.sidebar .widget, .main .widget { 
  border-bottom:1px dotted $bordercolor;
  margin:0 0 1.5em;
  padding:0 0 1.5em;
 }

.main .Blog { 
  border-bottom-width: 0;
}


/* Profile 
----------------------------------------------- */
.profile-img { 
  float: left;
  margin: 0 5px 5px 0;
  padding: 4px;
  border: 1px solid $bordercolor;
}

.profile-data {
  margin:0;
  text-transform:uppercase;
  letter-spacing:.1em;
  font: $postfooterfont;
  color: $sidebarcolor;
  font-weight: bold;
  line-height: 1.6em;
}

.profile-datablock { 
  margin:.5em 0 .5em;
}

.profile-textblock { 
  margin: 0.5em 0;
  line-height: 1.6em;
}

.profile-link { 
  font: $postfooterfont;
  text-transform: uppercase;
  letter-spacing: .1em;
}

/* Footer
----------------------------------------------- */
#footer {
  width:660px;
  clear:both;
  margin:0 auto;
  padding-top:15px;
  line-height: 1.6em;
  text-transform:uppercase;
  letter-spacing:.1em;
  text-align: center;
}

/** Page structure tweaks for layout editor wireframe */
body#layout #header { 
  margin-left: 0px;
  margin-right: 0px;
}
]]></b:skin>
  </head>

  <body>
  <div id='outer-wrapper'><div id='wrap2'>

    <!-- skip links for text browsers -->
    <span id='skiplinks' style='display:none;'>
      <a href='#main'>skip to main </a> |
      <a href='#sidebar'>skip to sidebar</a>
    </span>

    <div id='header-wrapper'>
      <b:section class='header' id='header' maxwidgets='1' showaddelement='no'>
<b:widget id='Header1' locked='true' title='Welcome to Ubuntu (Header)' type='Header'/>
</b:section>
    </div>
 
    <div id='content-wrapper'>

      <div id='crosscol-wrapper' style='text-align:center'>
        <b:section class='crosscol' id='crosscol' showaddelement='no'/>
      </div>

      <div id='main-wrapper'>
        <b:section class='main' id='main' showaddelement='no'>
<b:widget id='Blog1' locked='true' title='Blog Posts' type='Blog'/>
</b:section>
      </div>

      <div id='sidebar-wrapper'>
<script src='http://www.ubuntu.com/files/countdown/dist/display.js' type='text/javascript'/>
<noscript><img alt='Ubuntu 7.10 - Coming soon' height='164' id='countdownimage' src='http://www.ubuntu.com/files/countdown/dist/710countdown_default.png' width='199'/></noscript>
        <b:section class='sidebar' id='sidebar' preferred='yes'>
<b:widget id='Profile1' locked='false' title='About Me' type='Profile'/>
<b:widget id='BlogArchive1' locked='false' title='Blog Archive' type='BlogArchive'/>
</b:section>
<p>Template courtesy of <a href='http://welcometoubuntu.blogspot.com'>Welcome To Ubuntu.</a> Want this Blogger template? <a href='http://ubuntuforums.org/showthread.php?p=3525063'>Get it here!</a></p>
<p><a href='http://www.ubuntu.com/'><img alt='Ubuntu Logo' border='0' src='http://www.ubuntu.com/themes/ubuntu07/images/icon-ubuntu.png' title='Ubuntu Logo'/>Get Ubuntu</a>
<br/><a href='http://www.ubuntuforums.org/'><img alt='Ubuntu Logo' border='0' src='http://www.ubuntu.com/themes/ubuntu07/images/icon-ubuntu.png' title='Ubuntu Logo'/>Ubuntu Forums</a>
<br/><a href='http://www.spreadfirefox.com/?q=affiliates&amp;id=0&amp;t=222'><img alt='Foxkeh banners for Firefox 2' border='0' src='http://sfx-images.mozilla.org/affiliates/Buttons/firefox2/foxkeh-fx2-180x60.png' title='Foxkeh banners for Firefox 2'/></a>
<br/><a href='http://www.spreadfirefox.com/?q=affiliates&amp;id=0&amp;t=177'><img alt='Get Thunderbird!' border='0' src='http://sfx-images.mozilla.org/affiliates/thunderbird/reclaimyourinbox_small.png' title='Get Thunderbird!'/></a>
<br/><a href='http://www.openoffice.org'><img alt='OpenOffice.org Logo' border='0' src='http://contributing.openoffice.org/branding/images/logonew.gif' title='OpenOffice.org Logo'/></a></p>


      </div>

      <!-- spacer for skins that want sidebar and main to be the same height-->
      <div class='clear'> </div>

    </div> <!-- end content-wrapper -->

    <div id='footer-wrapper'>
      <b:section class='footer' id='footer'/>
    </div>

  </div></div> <!-- end outer-wrapper -->
<script type="text/javascript"><!--
 amzn_cl_tag="justinsblo04b-20";
 amzn_cl_preview=0;
 amzn_cl_categories="a,d,e,f";
//--></script>
<script type="text/javascript" src="http://cls.assoc-amazon.com/s/cls.js"></script>
</body>
</html>
```

---

### Post by por100pre1 on 2007-10-14
Thanks for sharing this! Unfortunately the link you provided doesn't work at this moment, it seems to be a blogger error. BTW, it would be good to have this moved to Art & Design. :)

---

### Post by justinmiller87 on 2007-10-14
> **por100pre1 said:**
> Thanks for sharing this! Unfortunately the link you provided doesn't work at this moment, it seems to be a blogger error. BTW, it would be good to have this moved to Art & Design. :)
You might find this humorous, the reason it broke was because I did somethig with my template earlier today that didn't affect the one above. When I was trying to add a script from Feedburner it messed it up. I removed it, and you should be able to view it again.

---

### Post by Lord Illidan on 2007-10-14
Not bad, however, I thought that you could have left a bigger margin between the brown background and the text, similar to the way this forum does.

---

### Post by por100pre1 on 2007-10-14
I agree with Lord Illidan. Add a margin to the text, that would make it perfect. :)

---

### Post by kostkon on 2007-10-14
Indeed you should put a little of whitespace between the text and the box edges. In your CSS you should add some padding.

---

### Post by justinmiller87 on 2007-10-15
After looking at it, and influenced by three people, I went ahead and made the change to the template. I also expanded the main text area out some to make it easier to read. Let me know what you think. Thanks!

---

### Post by k3lt01 on 2007-10-15
Apart from the things I dislike about ALL blog setups, I like how you have got yours looking.

The only thing I would comment on is the wasted space outside the "blog text" area, but EVERY blog I have seen is like that.

All in all well done.

P.S. I blogged on MySpace the other day about Ubuntu and Open Source, you can get to it through this link [http://www.myspace.com/m3rl1n68](http://www.myspace.com/m3rl1n68)

---

### Post by sankz on 2008-06-07
Hmm...
Nice one dude...
Btw, do you know any good xml editor in ubuntu?
I too want to create/edit some templates on one of my pc's that''s not connected to the net..
Thought i'll create one on it and then upload it to my site...

Thanx in advance...

---

