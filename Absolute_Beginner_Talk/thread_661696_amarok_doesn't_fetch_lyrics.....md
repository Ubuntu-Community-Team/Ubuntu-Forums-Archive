---
title: "amarok doesn't fetch lyrics...."
date: 2008-01-08
forum: Absolute Beginner Talk
---

### Post by someoneouthere on 2008-01-08
i had lyrics only 1-2 songs and then no lyrics at all 
the most of the times i start amarok prompts to run the lyrics script again...
i tried also-wiki lyrics the same
any ideas?

---

### Post by someoneouthere on 2008-01-08
after a while it shows a message:

The script 'Lyrc' exited with error code: 1

(details:)
```
 /usr/lib/ruby/1.8/net/http.rb:560:in `initialize': Connection timed out - connect(2) (Errno::ETIMEDOUT)
	from /usr/lib/ruby/1.8/net/http.rb:560:in `open'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/timeout.rb:48:in `timeout'
	from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
	from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
	from /usr/lib/ruby/1.8/net/http.rb:553:in `do_start'
	from /usr/lib/ruby/1.8/net/http.rb:542:in `start'
	from /usr/lib/ruby/1.8/net/http.rb:1032:in `request'
	from /usr/lib/ruby/1.8/net/http.rb:769:in `get'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:124:in `fetchLyrics'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:190
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:176:in `loop'
	from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:176

```

---

### Post by Nano Geek on 2008-01-08
It looks like it's saying that it can't connect. 
That either means that there's a problem with your connection (which I don't think is true since you're posting here ;) ) Or that the lyrics website is down.

Do you know which website it's trying to connect to?

---

### Post by someoneouthere on 2008-01-08
nope...

---

### Post by Nano Geek on 2008-01-08
Run this and post the output here. ```
cat /usr/lib/ruby/1.8/net/http.rb
```

---

### Post by mahiyar on 2008-01-08
Same problem here I guess the lyrics site is down today?

---

### Post by someoneouthere on 2008-01-08
here's the output:
   ```
 # true if the response has body.
    def HTTPResponse.body_permitted?
      self::HAS_BODY
    end

    def HTTPResponse.exception_type   # :nodoc: internal use only
      self::EXCEPTION_TYPE
    end
  end   # reopened after

  # :stopdoc:

  class HTTPUnknownResponse < HTTPResponse
    HAS_BODY = true
    EXCEPTION_TYPE = HTTPError
  end
  class HTTPInformation < HTTPResponse           # 1xx
    HAS_BODY = false
    EXCEPTION_TYPE = HTTPError
  end
  class HTTPSuccess < HTTPResponse               # 2xx
    HAS_BODY = true
    EXCEPTION_TYPE = HTTPError
  end
  class HTTPRedirection < HTTPResponse           # 3xx
    HAS_BODY = true
    EXCEPTION_TYPE = HTTPRetriableError
  end
  class HTTPClientError < HTTPResponse           # 4xx
    HAS_BODY = true
    EXCEPTION_TYPE = HTTPServerException   # for backward compatibility
  end
  class HTTPServerError < HTTPResponse           # 5xx
    HAS_BODY = true
    EXCEPTION_TYPE = HTTPFatalError    # for backward compatibility
  end

  class HTTPContinue < HTTPInformation           # 100
    HAS_BODY = false
  end
  class HTTPSwitchProtocol < HTTPInformation     # 101
    HAS_BODY = false
  end

  class HTTPOK < HTTPSuccess                            # 200
    HAS_BODY = true
  end
  class HTTPCreated < HTTPSuccess                       # 201
    HAS_BODY = true
  end
  class HTTPAccepted < HTTPSuccess                      # 202
    HAS_BODY = true
  end
  class HTTPNonAuthoritativeInformation < HTTPSuccess   # 203
    HAS_BODY = true
  end
  class HTTPNoContent < HTTPSuccess                     # 204
    HAS_BODY = false
  end
  class HTTPResetContent < HTTPSuccess                  # 205
    HAS_BODY = false
  end
  class HTTPPartialContent < HTTPSuccess                # 206
    HAS_BODY = true
  end

  class HTTPMultipleChoice < HTTPRedirection     # 300
    HAS_BODY = true
  end
  class HTTPMovedPermanently < HTTPRedirection   # 301
    HAS_BODY = true
  end
  class HTTPFound < HTTPRedirection              # 302
    HAS_BODY = true
  end
  HTTPMovedTemporarily = HTTPFound
  class HTTPSeeOther < HTTPRedirection           # 303
    HAS_BODY = true
  end
  class HTTPNotModified < HTTPRedirection        # 304
    HAS_BODY = false
  end
  class HTTPUseProxy < HTTPRedirection           # 305
    HAS_BODY = false
  end
  # 306 unused
  class HTTPTemporaryRedirect < HTTPRedirection  # 307
    HAS_BODY = true
  end

  class HTTPBadRequest < HTTPClientError                    # 400
    HAS_BODY = true
  end
  class HTTPUnauthorized < HTTPClientError                  # 401
    HAS_BODY = true
  end
  class HTTPPaymentRequired < HTTPClientError               # 402
    HAS_BODY = true
  end
  class HTTPForbidden < HTTPClientError                     # 403
    HAS_BODY = true
  end
  class HTTPNotFound < HTTPClientError                      # 404
    HAS_BODY = true
  end
  class HTTPMethodNotAllowed < HTTPClientError              # 405
    HAS_BODY = true
  end
  class HTTPNotAcceptable < HTTPClientError                 # 406
    HAS_BODY = true
  end
  class HTTPProxyAuthenticationRequired < HTTPClientError   # 407
    HAS_BODY = true
  end
  class HTTPRequestTimeOut < HTTPClientError                # 408
    HAS_BODY = true
  end
  class HTTPConflict < HTTPClientError                      # 409
    HAS_BODY = true
  end
  class HTTPGone < HTTPClientError                          # 410
    HAS_BODY = true
  end
  class HTTPLengthRequired < HTTPClientError                # 411
    HAS_BODY = true
  end
  class HTTPPreconditionFailed < HTTPClientError            # 412
    HAS_BODY = true
  end
  class HTTPRequestEntityTooLarge < HTTPClientError         # 413
    HAS_BODY = true
  end
  class HTTPRequestURITooLong < HTTPClientError             # 414
    HAS_BODY = true
  end
  HTTPRequestURITooLarge = HTTPRequestURITooLong
  class HTTPUnsupportedMediaType < HTTPClientError          # 415
    HAS_BODY = true
  end
  class HTTPRequestedRangeNotSatisfiable < HTTPClientError  # 416
    HAS_BODY = true
  end
  class HTTPExpectationFailed < HTTPClientError             # 417
    HAS_BODY = true
  end

  class HTTPInternalServerError < HTTPServerError   # 500
    HAS_BODY = true
  end
  class HTTPNotImplemented < HTTPServerError        # 501
    HAS_BODY = true
  end
  class HTTPBadGateway < HTTPServerError            # 502
    HAS_BODY = true
  end
  class HTTPServiceUnavailable < HTTPServerError    # 503
    HAS_BODY = true
  end
  class HTTPGatewayTimeOut < HTTPServerError        # 504
    HAS_BODY = true
  end
  class HTTPVersionNotSupported < HTTPServerError   # 505
    HAS_BODY = true
  end

  # :startdoc:


  class HTTPResponse   # reopen

    CODE_CLASS_TO_OBJ = {
      '1' => HTTPInformation,
      '2' => HTTPSuccess,
      '3' => HTTPRedirection,
      '4' => HTTPClientError,
      '5' => HTTPServerError
    }
    CODE_TO_OBJ = {
      '100' => HTTPContinue,
      '101' => HTTPSwitchProtocol,

      '200' => HTTPOK,
      '201' => HTTPCreated,
      '202' => HTTPAccepted,
      '203' => HTTPNonAuthoritativeInformation,
      '204' => HTTPNoContent,
      '205' => HTTPResetContent,
      '206' => HTTPPartialContent,

      '300' => HTTPMultipleChoice,
      '301' => HTTPMovedPermanently,
      '302' => HTTPFound,
      '303' => HTTPSeeOther,
      '304' => HTTPNotModified,
      '305' => HTTPUseProxy,
      '307' => HTTPTemporaryRedirect,

      '400' => HTTPBadRequest,
      '401' => HTTPUnauthorized,
      '402' => HTTPPaymentRequired,
      '403' => HTTPForbidden,
      '404' => HTTPNotFound,
      '405' => HTTPMethodNotAllowed,
      '406' => HTTPNotAcceptable,
      '407' => HTTPProxyAuthenticationRequired,
      '408' => HTTPRequestTimeOut,
      '409' => HTTPConflict,
      '410' => HTTPGone,
      '411' => HTTPLengthRequired,
      '412' => HTTPPreconditionFailed,
      '413' => HTTPRequestEntityTooLarge,
      '414' => HTTPRequestURITooLong,
      '415' => HTTPUnsupportedMediaType,
      '416' => HTTPRequestedRangeNotSatisfiable,
      '417' => HTTPExpectationFailed,

      '500' => HTTPInternalServerError,
      '501' => HTTPNotImplemented,
      '502' => HTTPBadGateway,
      '503' => HTTPServiceUnavailable,
      '504' => HTTPGatewayTimeOut,
      '505' => HTTPVersionNotSupported
    }

    class << HTTPResponse
      def read_new(sock)   #:nodoc: internal use only
        httpv, code, msg = read_status_line(sock)
        res = response_class(code).new(httpv, code, msg)
        each_response_header(sock) do |k,v|
          res.add_field k, v
        end
        res
      end

      private

      def read_status_line(sock)
        str = sock.readline
        m = /\AHTTP(?:\/(\d+\.\d+))?\s+(\d\d\d)\s*(.*)\z/in.match(str) or
          raise HTTPBadResponse, "wrong status line: #{str.dump}"
        m.captures
      end

      def response_class(code)
        CODE_TO_OBJ[code] or
        CODE_CLASS_TO_OBJ[code[0,1]] or
        HTTPUnknownResponse
      end

      def each_response_header(sock)
        while true
          line = sock.readuntil("\n", true).sub(/\s+\z/, '')
          break if line.empty?
          m = /\A([^:]+):\s*/.match(line) or
              raise HTTPBadResponse, 'wrong header line format'
          yield m[1], m.post_match
        end
      end
    end

    # next is to fix bug in RDoc, where the private inside class << self
    # spills out.
    public 

    include HTTPHeader

    def initialize(httpv, code, msg)   #:nodoc: internal use only
      @http_version = httpv
      @code         = code
      @message      = msg
      initialize_http_header nil
      @body = nil
      @read = false
    end

    # The HTTP version supported by the server.
    attr_reader :http_version

    # HTTP result code string. For example, '302'.  You can also
    # determine the response type by which response subclass the
    # response object is an instance of.
    attr_reader :code

    # HTTP result message. For example, 'Not Found'.
    attr_reader :message
    alias msg message   # :nodoc: obsolete

    def inspect
      "#<#{self.class} #{@code} #{@message} readbody=#{@read}>"
    end

    # For backward compatibility.
    # To allow Net::HTTP 1.1 style assignment
    # e.g.
    #    response, body = Net::HTTP.get(....)
    # 
    def to_ary
      warn "net/http.rb: warning: Net::HTTP v1.1 style assignment found at #{caller(1)[0]}; use `response = http.get(...)' instead." if $VERBOSE
      res = self.dup
      class << res
        undef to_ary
      end
      [res, res.body]
    end

    #
    # response <-> exception relationship
    #

    def code_type   #:nodoc:
      self.class
    end

    def error!   #:nodoc:
      raise error_type().new(@code + ' ' + @message.dump, self)
    end

    def error_type   #:nodoc:
      self.class::EXCEPTION_TYPE
    end

    # Raises HTTP error if the response is not 2xx.
    def value
      error! unless self.kind_of?(HTTPSuccess)
    end

    #
    # header (for backward compatibility only; DO NOT USE)
    #

    def response   #:nodoc:
      warn "#{caller(1)[0]}: warning: HTTPResponse#response is obsolete" if $VERBOSE
      self
    end

    def header   #:nodoc:
      warn "#{caller(1)[0]}: warning: HTTPResponse#header is obsolete" if $VERBOSE
      self
    end

    def read_header   #:nodoc:
      warn "#{caller(1)[0]}: warning: HTTPResponse#read_header is obsolete" if $VERBOSE
      self
    end

    #
    # body
    #

    def reading_body(sock, reqmethodallowbody)  #:nodoc: internal use only
      @socket = sock
      @body_exist = reqmethodallowbody && self.class.body_permitted?
      begin
        yield
        self.body   # ensure to read body
      ensure
        @socket = nil
      end
    end

    # Gets entity body.  If the block given, yields it to +block+.
    # The body is provided in fragments, as it is read in from the socket.
    #
    # Calling this method a second or subsequent time will return the
    # already read string.
    #
    #   http.request_get('/index.html') {|res|
    #     puts res.read_body
    #   }
    #
    #   http.request_get('/index.html') {|res|
    #     p res.read_body.object_id   # 538149362
    #     p res.read_body.object_id   # 538149362
    #   }
    #
    #   # using iterator
    #   http.request_get('/index.html') {|res|
    #     res.read_body do |segment|
    #       print segment
    #     end
    #   }
    #
    def read_body(dest = nil, &block)
      if @read
        raise IOError, "#{self.class}\#read_body called twice" if dest or block
        return @body
      end
      to = procdest(dest, block)
      stream_check
      if @body_exist
        read_body_0 to
        @body = to
      else
        @body = nil
      end
      @read = true

      @body
    end

    # Returns the entity body.
    #
    # Calling this method a second or subsequent time will return the
    # already read string.
    #
    #   http.request_get('/index.html') {|res|
    #     puts res.body
    #   }
    #
    #   http.request_get('/index.html') {|res|
    #     p res.body.object_id   # 538149362
    #     p res.body.object_id   # 538149362
    #   }
    #
    def body
      read_body()
    end

    alias entity body   #:nodoc: obsolete

    private

    def read_body_0(dest)
      if chunked?
        read_chunked dest
        return
      end
      clen = content_length()
      if clen
        @socket.read clen, dest, true   # ignore EOF
        return
      end
      clen = range_length()
      if clen
        @socket.read clen, dest
        return
      end
      @socket.read_all dest
    end

    def read_chunked(dest)
      len = nil
      total = 0
      while true
        line = @socket.readline
        hexlen = line.slice(/[0-9a-fA-F]+/) or
            raise HTTPBadResponse, "wrong chunk size line: #{line}"
        len = hexlen.hex
        break if len == 0
        @socket.read len, dest; total += len
        @socket.read 2   # \r\n
      end
      until @socket.readline.empty?
        # none
      end
    end

    def stream_check
      raise IOError, 'attempt to read body out of block' if @socket.closed?
    end

    def procdest(dest, block)
      raise ArgumentError, 'both arg and block given for HTTP method' \
          if dest and block
      if block
        ReadAdapter.new(block)
      else
        dest || ''
      end
    end

  end


  # :enddoc:

  #--
  # for backward compatibility
  class HTTP
    ProxyMod = ProxyDelta
  end
  module NetPrivate
    HTTPRequest = ::Net::HTTPRequest
  end

  HTTPInformationCode = HTTPInformation
  HTTPSuccessCode     = HTTPSuccess
  HTTPRedirectionCode = HTTPRedirection
  HTTPRetriableCode   = HTTPRedirection
  HTTPClientErrorCode = HTTPClientError
  HTTPFatalErrorCode  = HTTPClientError
  HTTPServerErrorCode = HTTPServerError
  HTTPResponceReceiver = HTTPResponse

end   # module Net

```

---

### Post by nidelius on 2008-01-08
I can confirm this bug

The script 'Lyrc' exited with error code: 1


Clicking on 'Details' button shows:
Code:
/usr/lib/ruby/1.8/net/http.rb:560:in `initialize': Connection timed out - connect(2) (Errno::ETIMEDOUT)
   from /usr/lib/ruby/1.8/net/http.rb:560:in `open'
   from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
   from /usr/lib/ruby/1.8/timeout.rb:48:in `timeout'
   from /usr/lib/ruby/1.8/timeout.rb:76:in `timeout'
   from /usr/lib/ruby/1.8/net/http.rb:560:in `connect'
   from /usr/lib/ruby/1.8/net/http.rb:553:in `do_start'
   from /usr/lib/ruby/1.8/net/http.rb:542:in `start'
   from /usr/lib/ruby/1.8/net/http.rb:1032:in `request'
   from /usr/lib/ruby/1.8/net/http.rb:769:in `get'
   from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:127:in `fetchLyrics'
   from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:193
   from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179:in `loop'
   from /usr/share/apps/amarok/scripts/lyrics_lyrc/lyrics_lyrc.rb:179

---

### Post by mahiyar on 2008-01-09
The lyric site is up and running today.

---

### Post by apricot on 2008-05-24
Same to me. Anybody solved this problem?

---

### Post by Nano Geek on 2008-05-26
It sounded like the site itself was down the first time, perhaps it has gone down again.

---

### Post by mcpork86 on 2008-07-05
I have the same problem now after an update of the system. Had it a year ago or so already but then it went away, I don't know why. I'm pretty sure the lyrics server is not down, so there must be another reason? Can anyone tell me?

Thanks!

---

### Post by mcpork86 on 2008-07-05
ok, with wiki-lyrics plugin script it now works, apparently the server was indeed down!

---

