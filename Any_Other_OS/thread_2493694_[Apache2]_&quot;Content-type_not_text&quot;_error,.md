---
title: "[Apache2] &quot;Content-type not text&quot; error, but it's text/html"
date: 2023-12-21
forum: Any Other OS
---

### Post by sdsurfer on 2023-12-21
If this is an inappropriate question feel free to delete. Just moved my wife's old legacy site to a new VPS server on almaLinux running cPanel/WHM. I haven't done a lot of customization, things just seem to work except this.

**The problem: getting a content-type error from Apache2 when I know the output of this script includes content type headers.**

```

[Thu Dec 21 10:59:34.717822 2023] [include:error] [pid 738483:tid 23353639089920] [client (ip address)] unable to include potential exec "/cgi-bin/articles_menu.cgi?c=name-of-the-page" in parsed file /home/(user)/public_html/name-of-the-page.shtml, **content type not text/***, referer: https://www.(user).com/

```

Starts here: 

```

<!--#include virtual="/cgi-bin/articles_menu.cgi?c=name-of-the-page" -->

```

The script is extremely simple and it works, and has for years, depending on what page you're on it opens and parses a plain text file and skips "name of the page" before outputting the menu like so:

```

 if ($ENV{'QUERY_STRING'}) {
   print "content-type: text/html\n\n";
   print "$out";
 }

```

As mentioned I've confirmed this works via cli and you can request the URL from a browser like
```

aitch-tee-tee-pea-ess//example.com/cgi-bin/articles_menu.cgi?c=name-of-the-page

```

When you request that URL, FF Inspector says the output headers are content-type text/html.

I have confirmed indeed $out is populated and working. Appropriate handlers are operational. Both SSI's and scripts are working fine. Reviewed the Apache docs and not seeing anything relevant.

Am I missing an Apache config that addresses "potential exec?" (I doubt that's the problem but . . . ) Does anyone have any ideas where I could look?

A few specs:

cPanel Version     116.0 (build 7)
Apache Version     2.4.58
Perl Version    5.26.3

User Defined Apache Handlers
application/x-httpd-ea-php74     .php .php7 .phtml    (This site is pre-PHP, that's how old school it is) 
server-parsed     .html     
server-parsed     .shtml .html 

System Apache Handlers
cgi-script     .cgi .pl .plx .ppl .perl
server-parsed     .shtml

---

### Post by howefield on 2023-12-21
Thread moved to the "*Any Other OS!* forum

---

### Post by sdsurfer on 2023-12-21
> **howefield said:**
> Thread moved to the "*Any Other OS!* forum

Thank you, I did a search and found some other posts in programming.

---

### Post by sdsurfer on 2023-12-22
To anyone coming to this thread to solve the error . . . 

I experimented with a lot of stuff from both WHM and this user's cPanel, namely around the option** IncludesNoExec**. This really shouldn't have any effect because we're using include virtual, not include exec, but no matter - enabling that option only causes the server to ignore the include line (not parsiing the include, you see it in source code of the page as it is above.)
[B]
What fixed it for me[/B] was to simply add Includes to the user's root .htaccess

```

Options +Includes

```

I would have never thought to look there because any other SSI include that is plain text or html was included and parsed just fine.

This is perfect if you don't want to mod the Apache httpd.conf (it warns at the top it could potentially be overwritten by cPanel.) But of course you do have to allow the user's directory to allow overrides.

---

### Post by biledk on 2024-03-22
Hi sd surfer, thanks for the post, I had a:
Content is not loading because its MIME type, "text/html" is not "text/css"

Fixed it by deleting:
[COLOR=var(--highlight-keyword)][FONT=inherit]if[/FONT][/COLOR] (process.[FONT=inherit]env[/FONT].[FONT=inherit]NODE_ENV[/FONT] == [COLOR=var(--highlight-variable)][FONT=inherit]'production'[/FONT][/COLOR]) {
    app.[COLOR=var(--highlight-literal)][FONT=inherit]use[/FONT][/COLOR](express.[COLOR=var(--highlight-literal)][FONT=inherit]static[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]'client/build'[/FONT][/COLOR]));
    }
    
 app.[COLOR=var(--highlight-literal)][FONT=inherit]get[/FONT][/COLOR]([COLOR=var(--highlight-variable)][FONT=inherit]'*'[/FONT][/COLOR], [FONT=inherit]([FONT=inherit]req, res[/FONT]) =>[/FONT] {
  res.[COLOR=var(--highlight-literal)][FONT=inherit]sendFile[/FONT][/COLOR](path.[COLOR=var(--highlight-literal)][FONT=inherit]join[/FONT][/COLOR](__dirname, [COLOR=var(--highlight-variable)][FONT=inherit]'client'[/FONT][/COLOR], [COLOR=var(--highlight-variable)][FONT=inherit]'build'[/FONT][/COLOR], [COLOR=var(--highlight-variable)][FONT=inherit]'index.html'[/FONT][/COLOR]))
});
In the server.js file

---

