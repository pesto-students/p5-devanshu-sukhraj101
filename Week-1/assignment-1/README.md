What is the main functionality of the browser?
---------------

Web Browser Definition: A software application used to access information on the World Wide Web is called a Web Browser. When a user requests some information, the web browser fetches the data from a web server and then displays the webpage on the user’s screen.

Functions of Web Browser:

* The main function is to retrieve information from the World Wide Web and making it available for users.
* Visiting any website can be done using a web browser. When a URL is entered in a browser, the web server takes us to that website.
* It makes Internet surfing easy as once we reach a website we can easily check the hyperlinks and get more and more useful data online
* Multiple webpages can be opened at the same time on a web browser.
* Options like back, forward, reload, stop reload, home, etc. are available on these web browsers, which make using them easy and convenient.

High Level Components of a browser
---------------

The browser's main components are:
* `The user interface:` this includes the address bar, back/forward button, bookmarking menu, etc. Every part of the browser display except the window where you see the requested page.
* `The browser engine:` marshals actions between the UI and the rendering engine.
* `The rendering engine:` responsible for displaying requested content. For example if the requested content is HTML, the rendering engine parses HTML and CSS, and displays the parsed content on the screen.
* `Networking:` for network calls such as HTTP requests, using different implementations for different platform behind a platform-independent interface.
* `UI backend:` used for drawing basic widgets like combo boxes and windows. This backend exposes a generic interface that is not platform specific. Underneath it uses operating system user interface methods.
* `JavaScript interpreter:` Used to parse and execute JavaScript code.
* `Data storage:` This is a persistence layer. The browser may need to save all sorts of data locally, such as cookies. Browsers also support storage mechanisms such as localStorage, IndexedDB, WebSQL and FileSystem.

![alt text](https://web-dev.imgix.net/image/T4FyVKpzu4WKF1kBNvXepbi08t52/PgPX6ZMyKSwF6kB8zIhB.png)


Rendering engine and its use
--------------------

The responsibility of the rendering engine is well… Rendering, that is display of the requested contents on the browser screen.
By default the rendering engine can display HTML and XML documents and images. It can display other types of data via plug-ins or extension.

Different browsers use different rendering engines: Internet Explorer uses Trident, Firefox uses Gecko, Safari uses WebKit. Chrome and Opera (from version 15) use Blink, a fork of WebKit.

![alt text](https://web-dev.imgix.net/image/T4FyVKpzu4WKF1kBNvXepbi08t52/bPlYx9xODQH4X1KuUNpc.png?auto=format&w=650)


Parsers (HTML, CSS)
--------------------

Parsing a document means translating it to a structure the code can use. The result of parsing is usually a tree of nodes that represent the structure of the document. This is called a parse tree or a syntax tree.

`HTML Parser:` The job of the HTML parser is to parse the HTML markup into a parse tree. When the parser is created the Document object is created.

`CSS Parser:` When the browser encounters a CSS stylesheet (either embedded or external), it needs to parse the text into something it can use for style layouts and paints. The data structure that the browser turns CSS into is creatively named the CSSOM, — the CSS Object Model. The CSS parser has to read nested selectors from right-to-left in order to guarantee that they end up underneath the correct nodes.


Script Processors
--------------------

The script processor executes Javascript code to process an event. The processor uses a pure Go implementation of ECMAScript 5.1 and has no external dependencies. 
This can be useful in situations where one of the other processors doesn’t provide the functionality you need to filter events.

The script processor has the following configuration settings:

`lang`, `tag`, `source`, `file`, `files`, `params`, `tag_on_exception`, `timeout`, `max_cached_sessions`

Tree construction
--------------------




Order of script processing
--------------------

Depending on the type of object, the task may have more than one Process page on which you can write scripts. The scripts in the Process pages are processed in the following order:

* Pre-Process page and Process page
* Child Post Process page
* Post Process page


Layout and Painting
--------------------

## Layout

The fourth step in the critical rendering path is running layout on the render tree to compute the geometry of each node. Layout is the process by which the width, height, and location of all the nodes in the render tree are determined, plus the determination of the size and position of each object on the page. Reflow is any subsequent size and position determination of any part of the page or the entire document.

## Paint

The last step in the critical rendering path is painting the individual nodes to the screen, the first occurrence of which is called the first meaningful paint. In the painting or rasterization phase, the browser converts each box calculated in the layout phase to actual pixels on the screen. Painting involves drawing every visual part of an element to the screen, including text, colors, borders, shadows, and replaced elements like buttons and images. The browser needs to do this super quickly.