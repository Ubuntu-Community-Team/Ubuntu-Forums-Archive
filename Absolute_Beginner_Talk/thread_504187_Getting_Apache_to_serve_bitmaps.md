---
title: "Getting Apache to serve bitmaps"
date: 2007-07-18
forum: Absolute Beginner Talk
---

### Post by bernie1442 on 2007-07-18
I have recently installed Apache2 on a test server I have set up with Dapper.  I am running into a small problem serving images.  The server will not serve bitmap images correctly.  When I try to view a bitmap with a browser, the browser tries to download the file, it does not display the image.  This is happening with both IE and Firefox.    I have renamed the file as a JPEG and I am able to view the image fine.  I do not see anything being written to the error log and the access log entires look identical for the bitmap and JPEG.  Any help would be greatly appreciated



[18/Jul/2007:21:06:38 -0400] "GET /test.jpg HTTP/1.1" 304 - "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-U
S; rv:1.8.1.5) Gecko/20070713 Firefox/2.0.0.5"

[18/Jul/2007:21:06:57 -0400] "GET /test.bmp HTTP/1.1" 304 - "-" "Mozilla/5.0 (Windows; U; Windows NT 5.1; en-U
S; rv:1.8.1.5) Gecko/20070713 Firefox/2.0.0.5"


/etc/mime.types
..
..
image/bmp                                       bmp   <------I added this
image/cgm
image/g3fax
image/gif                                       gif
image/ief                                       ief
image/jpeg                                      jpeg jpg jpe
image/naplps
image/pcx                                       pcx
image/png                                       png
image/prs.btif
image/prs.pti
image/svg+xml                                   svg svgz
image/tiff                                      tiff tif
image/vnd.cns.inf2
image/vnd.djvu                                  djvu djv
image/vnd.dwg
image/vnd.dxf
image/vnd.fastbidsheet
image/vnd.fpx
image/vnd.fst
image/vnd.fujixerox.edmics-mmr
image/vnd.fujixerox.edmics-rlc
image/vnd.mix
image/vnd.net-fpx
image/vnd.svf
image/vnd.wap.wbmp                              wbmp
image/vnd.xiff
image/x-cmu-raster                              ras
image/x-coreldraw                               cdr
image/x-coreldrawpattern                        pat
image/x-coreldrawtemplate                       cdt
image/x-corelphotopaint                         cpt
image/x-icon                                    ico
image/x-jg                                      art
image/x-jng                                     jng
image/x-ms-bmp                                  bmp
image/x-photoshop                               psd
image/x-portable-anymap                         pnm
image/x-portable-bitmap                         pbm
image/x-portable-graymap                        pgm
image/x-portable-pixmap                         ppm
image/x-rgb                                     rgb
image/x-xbitmap                                 xbm
image/x-xpixmap                                 xpm
image/x-xwindowdump                             xwd
..
..

---

### Post by DBStevens on 2007-07-19
The problem is actually on the browser end not the server.

In order for the browser to render an image it must have a bit of code to handle it and the proper linkage as to what file type uses what code.  If it has that code it will display the image otherwise it will treat it as a file to download.

All the server does is provide the type and the file in response to the browsers request. 


Sending request:

GET /yyyyyy1.jpg HTTP/1.1
Host: [www.example.com](www.example.com)
User-Agent: Mozilla/5.0 (X11; U; Linux i686; en-US; rv:1.8.1.4) Gecko/20061201 Firefox/2.0.0.4 (Ubuntu-feisty)
Connection: close

&#8226; Finding host IP address...
&#8226; Host IP address = tt.tt.tt.tt
&#8226; Finding TCP protocol...
&#8226; Binding to local socket...
&#8226; Connecting to host...
&#8226; Sending request...
&#8226; Waiting for response...
Receiving Header:
HTTP/1.1·200·OK(CR)(LF)
Date:·Thu,·19·Jul·2007·14:45:11·GMT(CR)(LF)
Server:·Apache/1.3.33·(Unix)·mod_auth_passthrough/1.8·mod_log_bytes/1.2·mod_bwlimited/1.4·PHP/4.3.9·FrontPage/5.0.2.2635·mod_ssl/2.8.22·OpenSSL/0.9.7a(CR)(LF)
Last-Modified:·Thu,·05·Jul·2007·19:03:10·GMT(CR)(LF)
ETag:·"80023-e175-468d406e"(CR)(LF)
Accept-Ranges:·bytes(CR)(LF)
Content-Length:·57717(CR)(LF)
Connection:·close(CR)(LF)
Content-Type:·image/jpeg(CR)(LF)
(CR)(LF)
End of Header (Length = 373)
&#8226; Elapsed time so far: 0 seconds
&#8226; Waiting for additional response until connection closes...
Total bytes received = 58090
Elapsed time so far: 0 seconds
Content (Length = 57717):

       0: FFD8FFE000104A46 494600010101012C &#8226;&#8226;&#8226;&#8226;&#8226;&#8226;JF IF&#8226;&#8226;&#8226;&#8226;&#8226;,
      10: 012C0000FFDB0043 0005030404040305 &#8226;,&#8226;&#8226;&#8226;&#8226;&#8226;C &#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;&#8226;


Note the header received from the server indicating the type of content that follows:

Content-Type:·image/jpeg(CR)(LF)


So you need the server set to send the correct type wich you did but the other end has to know what to use to display a particular type of content.

---

### Post by jsweeney on 2007-09-02
I've been designing websites for 12 years, and was not aware bitmaps could be displayed in a browser. My understanding is that the supported formats are restricted to JPEG, GIF, and PNG. Of course, I've been under the Windows rock, so I am not aware what Apache2 is capable of.

---

### Post by DBStevens on 2007-09-03
jsweeney,

It isn't a server issue in this case, it is a browser issue.   The server sends a header with the file type associated with the file extension, then the browser needs to know what to do with it.

BTW google rick swain, and try looking at a request through his http viewer.

---

