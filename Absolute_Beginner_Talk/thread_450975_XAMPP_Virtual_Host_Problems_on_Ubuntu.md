---
title: "XAMPP Virtual Host Problems on Ubuntu"
date: 2007-05-21
forum: Absolute Beginner Talk
---

### Post by giallofever on 2007-05-21
Hi. Any websites and/or tutorials for complete newcomers to virtual hosting. Every site I Googled does it a different way. I have tried posting at XAMPP, but little support, so I thought I'd give it a try here. I have XAMPP up and running fine. Type in localhost and I'm there. I now want to virtual host a site or two, (just type [www.test.com](www.test.com), etc. and have it route to my localhost.) I have edited my vhosts and httpd.conf files but no go.

Here is the pertinent part of /opt/lampp/etc/httpd.conf

> # Supplemental configuration
#
# The configuration files in the etc/extra/ directory can be 
# included to add extra features or to modify the default configuration of 
# the server, or you may simply copy their contents here and change as 
# necessary.

# Server-pool management (MPM specific)
#Include etc/extra/httpd-mpm.conf

# Multi-language error messages
#Include etc/extra/httpd-multilang-errordoc.conf

# Fancy directory listings
Include etc/extra/httpd-autoindex.conf

# Language settings
#Include etc/extra/httpd-languages.conf

# User home directories
#Include etc/extra/httpd-userdir.conf

# Real-time info on requests and configuration
#Include etc/extra/httpd-info.conf

# Virtual hosts
Include etc/extra/httpd-vhosts.conf

# Local access to the Apache HTTP Server Manual
#Include etc/extra/httpd-manual.conf

# Distributed authoring and versioning (WebDAV)
#Include etc/extra/httpd-dav.conf

# Various default settings
Include etc/extra/httpd-default.conf

# Secure (SSL/TLS) connections
<IfModule ssl_module>
# XAMPP
<IfDefine SSL>
Include etc/extra/httpd-ssl.conf
</IfDefine>
</IfModule>
#
# Note: The following must must be present to support
#       starting without SSL on platforms with no /dev/random equivalent
#       but a statically compiled-in mod_ssl.
#
<IfModule ssl_module>
SSLRandomSeed startup builtin

And here is the /opt/lampp/etc/extra/httpd-vhosts.conf file

> #
# Virtual Hosts
#
# If you want to maintain multiple domains/hostnames on your
# machine you can setup VirtualHost containers for them. Most configurations
# use only name-based virtual hosts so the server doesn't need to worry about
# IP addresses. This is indicated by the asterisks in the directives below.
#
# Please see the documentation at 
# <URL:http://httpd.apache.org/docs/2.2/vhosts/>
# for further details before you try to setup virtual hosts.
#
# You may use the command line option '-S' to verify your virtual host
# configuration.

#
# Use name-based virtual hosting.
#
NameVirtualHost *:80

#
# VirtualHost example:
# Almost any Apache directive may go into a VirtualHost container.
# The first VirtualHost section is used for all requests that do not
# match a ServerName or ServerAlias in any <VirtualHost> block.
#
<VirtualHost *:80>
    ServerAdmin [email]webmaster@test.com[/email]
    VirtualDocumentRoot /home/websites/test.com
    ServerName test.com
    ErrorLog logs/test.com-error_log
    CustomLog logs/test.com-access_log common
    DirectoryIndex index.php index.htm index.html index.cgi
</VirtualHost>

Anybody familiar with this or have this working?

---

### Post by benmoreassynt on 2007-05-22
Have you restarted Apache (using /opt/lampp/lampp restart for XAMPP)? It won't work until restarted otherwise.

Have you also edited your hosts file? (/etc/hosts).

The first line will need to read:

127.0.0.1 localhost test.com

Other than that it looks ok, and typing in 'test.com' to the browser should take you to localhost.

---

### Post by gdoermann on 2008-03-19
How do I modify the /etc/hosts if I am using a Dynamic DNS service... say zoneedit.com?

---

