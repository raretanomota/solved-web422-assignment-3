Download Link: https://assignmentchef.com/product/solved-web422-assignment-3
<br>
To continue to work with our “Sales” API (from Assignment 1) on the client-side to produce a rich user interface for accessing data.  For this assignment, we will be leveraging our knowledge of React create an interface for <em>viewing</em> sales.  <strong>Please Note</strong>: You’re free to style your app however you wish, however the following specification outlines how we can use the <a href="https://react-bootstrap-v3.netlify.com/">React</a><a href="https://react-bootstrap-v3.netlify.com/">–</a><a href="https://react-bootstrap-v3.netlify.com/">Bootstrap v3 Components</a><a href="https://react-bootstrap-v3.netlify.com/">.</a>  If you wish to add additional images, styles or functionality, please go ahead.

Sample Solution:

You can see a video of the solution running at the link below:




<a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A3/A3.mp4">https://ict.senecacollege.ca/~patrick.crawford/shared/summer</a><a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A3/A3.mp4">–</a><a href="https://ict.senecacollege.ca/~patrick.crawford/shared/summer-2020/web422/A3/A3.mp4">2020/web422/A3/A3.mp4</a>




<h1>Step 1: Creating a React App &amp; Adding 3<sup>rd</sup> Party Components</h1>

The first step is to create a new directory for your solution, open it in Visual Studio Code and open the integrated terminal:

<ul>

 <li>Next, proceed to create a new react app by using “<a href="https://www.npmjs.com/package/create-react-app">create</a><a href="https://www.npmjs.com/package/create-react-app">–</a><a href="https://www.npmjs.com/package/create-react-app">react</a><a href="https://www.npmjs.com/package/create-react-app">–</a><a href="https://www.npmjs.com/package/create-react-app">app</a><a href="https://www.npmjs.com/package/create-react-app">“</a>. If you do not have it installed on your local machine yet, it can be added using the command “npm install -g create-react-app”.</li>

 <li>Once the tool has finished creating your React App, be sure to “cd” into your new app directory and install the following modules using npm: o react-router-dom o <a href="/cdn-cgi/l/email-protection" class="__cf_email__" data-cfemail="691b0c080a1d440b06061d1a1d1b08192959475a5a4758">[email protected]</a> o react-router-bootstrap</li>

 <li>To ensure that our newly-added Bootstrap (v3) components render properly, we must add the correct CSS file globally to our “public/index.html” file (before the “manifest”), ie:</li>

</ul>

o &lt;link rel=”stylesheet” href=”https://stackpath.bootstrapcdn.com/bootstrap/3.4.1/css/bootstrap.min.css” integrity=”sha384HSMxcRTRxnN+Bdg0JdbxYKrThecOKuH5zCYotlSAcp1+c8xmyTe9GYg1l9a69psu” crossorigin=”anonymous”&gt;

<ul>

 <li>Next, we must clear out (delete) the CSS content from both “App.css” and “index.css”, since we won’t be using any of those rules within our new app. Once this is complete, place the following single line of css within the “index.css” file (this will ensure that any table with class “table-hover” has the “Pointer” cursor:</li>

</ul>




<strong>table.table-hover:hover{ cursor: pointer; }</strong>







<h1>Step 2: Route Component “Skeletons”</h1>

For the next part of the assignment, we’ll add all of the components that our routes will use as well as create a navbar that persists across all routes to help the user navigate our app.

To Begin, add the following components, in separate files (using the naming convention <strong><em>ComponentName.js</em></strong>) within the “src” directory.  Each of these components must be implemented using a “class” (instead of a function).

<ul>

 <li><strong>Sales</strong> – outputs: &lt;div&gt;&lt;h1&gt;Sales&lt;/h1&gt;&lt;/div&gt;</li>

 <li><strong>Sale</strong> – outputs: &lt;div&gt;&lt;h1&gt;Sale id: <strong><em>id</em></strong>&lt;/h1&gt;&lt;/div&gt; where <strong><em>id</em></strong> is a value that will be available in “props” thanks to our routing configuration (see: Step 4)</li>

 <li><strong>NotFound</strong> – outputs &lt;div&gt;&lt;h1&gt;Not Found&lt;/h1&gt;&lt;p&gt;We can’t find what you’re looking for…&lt;/p&gt;&lt;/div&gt; (<strong>Note</strong>:</li>

</ul>

please feel free to change this up to something more fun).

<strong> </strong>

<h1>Step 3: App Component &amp; NavBar</h1>

Before we add routing to our application, we must first do some work with the “App” component:

<ul>

 <li>To begin, add the following import statements

  <ul>

   <li>{ Navbar, Nav, NavItem, NavDropdown, MenuItem, FormGroup, FormControl, Grid, Row, Col } from <strong>react-bootstrap</strong> o { Link, Switch, Redirect, Route } from <strong>react-router-dom</strong></li>

   <li>{ LinkContainer } from <strong>react-router-bootstrap</strong></li>

  </ul></li>

 <li>Next, remove all of the contents from the return statement and instead simply return “null” (we will change this soon)</li>

 <li>Next, delete the import for “logo” – we won’t be using the “logo” for our application. o You can also delete the src/logo.svg file</li>

 <li>Now we must convert our App component into a “class” with the following default “state” values (defined in the constructor)

  <ul>

   <li>recentlyViewed: [] o searchId: “”</li>

  </ul></li>

 <li>Before we are done, we must add two methods to our class; the first of which is called called <strong>viewedSale(id)</strong> with the following specification – <strong>NOTE</strong>: this method must have the value of “this” correctly bound to the function in the constructor.</li>

</ul>




Once “this” is correctly bound in the constructor, the <strong>viewedSale(id)</strong> function must be implemented according to the following specification:

<ul>

 <li>Pushes the value of “id” into the “recentlyViewed” array in the <strong>state </strong>only if it’s not already in the array, ie:</li>

</ul>




if(state.recentlyViewed.indexOf(id) === -1) {   state.recentlyViewed.push(id);

}




<ul>

 <li>Updates the <strong>state</strong> with the updated “recentlyViewed” array, causing the component to <strong>render</strong>.</li>

</ul>




This will help us track which sales have been recently viewed by the client, so that they can easily recall them later.

<ul>

 <li>The next method is <strong>updateSearchId(e)</strong> – <strong>NOTE</strong>: this method must have the value of “this” correctly bound to the function in the constructor.</li>

</ul>




Once “this” is correctly bound in the constructor, the <strong>updateSearchId(e)</strong> function must be implemented according to the following specification:

<ul>

 <li>Updates the value of “searchId” in the <strong>state</strong> using the target.<strong>value </strong>value, causing the component to <strong>render</strong>.</li>

</ul>




This will help us update the “Search” button (link) in the navbar to the current “searchId”




Now that our App component has been converted into a class with a “state” to manage recently viewed sales, we can proceed to update the “render” method to show a <a href="https://react-bootstrap-v3.netlify.com/components/navbar/">navbar built using React</a><a href="https://react-bootstrap-v3.netlify.com/components/navbar/">–</a><a href="https://react-bootstrap-v3.netlify.com/components/navbar/">Bootstrap 3 components</a><a href="https://react-bootstrap-v3.netlify.com/components/navbar/">.</a>




<ul>

 <li>Add the following JSX code to the return value of the <strong>render</strong> method of our App component:</li>

</ul>




&lt;div&gt;

&lt;Navbar inverse collapseOnSelect staticTop&gt;

&lt;Navbar.Header&gt;

&lt;LinkContainer to=”/”&gt;

&lt;Navbar.Brand&gt;

WEB422 – Sales

&lt;/Navbar.Brand&gt;

&lt;/LinkContainer&gt;

&lt;Navbar.Toggle /&gt;

&lt;/Navbar.Header&gt;

&lt;Navbar.Collapse&gt;

&lt;Nav&gt;

&lt;LinkContainer to=”/Sales”&gt;

&lt;NavItem&gt;All Sales&lt;/NavItem&gt;

&lt;/LinkContainer&gt;

&lt;NavDropdown title=”Previously Viewed” id=”basic-nav-dropdown”&gt;       {this.state.recentlyViewed.length &gt; 0 ?          this.state.recentlyViewed.map((id, index)=&gt;(            &lt;LinkContainer to={`/Sale/${id}`} key={index}&gt;

&lt;MenuItem &gt;Sale: {id}&lt;/MenuItem&gt;           &lt;/LinkContainer&gt; )) :

&lt;MenuItem&gt;…&lt;/MenuItem&gt;}

&lt;/NavDropdown&gt;

&lt;/Nav&gt;

&lt;Navbar.Form pullRight&gt;       &lt;FormGroup&gt;

&lt;FormControl type=”text” onChange={this.updateSearchId} placeholder=”Sale ID” /&gt;       &lt;/FormGroup&gt;{‘ ‘}

&lt;Link className=”btn btn-default” to={“/Sale/” + this.state.searchId}&gt;Search&lt;/Link&gt;

&lt;/Navbar.Form&gt;

&lt;/Navbar.Collapse&gt;

&lt;/Navbar&gt;

&lt;/div&gt;




<h1>Step 4: Adding Routes</h1>

With our Navbar in place and our App component all set up, we can now proceed to add the routes to our application:

<ul>

 <li>In your src/<strong>js</strong> file, import the “BrowserRouter” component and use it to wrap the &lt;App /&gt; Component (ie: the &lt;App /&gt; Component will be the only child of the &lt;BrowserRouter&gt;&lt;/BrowserRouter&gt; Component</li>

 <li>Next, in the return value of the <strong>render</strong> method for the &lt;App /&gt; Component, add the following code <strong>beneath</strong> the navbar:</li>

</ul>




<strong>&lt;Grid&gt; </strong>

<strong>  &lt;Row&gt; </strong>

<strong>    &lt;Col md={12}&gt; </strong>

<strong>       </strong>

<strong>    &lt;/Col&gt; </strong>

<strong>  &lt;/Row&gt; </strong>

<strong>&lt;/Grid&gt; </strong>

<strong> </strong>

The above code simply sets up a Bootstrap 3 grid with a single column with width “12” (on “medium” and larger devices)

<strong> </strong>

<ul>

 <li>Inside the &lt;Col&gt;&lt;/Col&gt; Component, add your &lt;Switch&gt;&lt;/Switch&gt; Component as well as configuration for the following routes:

  <ul>

   <li>“/” – Redirects to the “/Sales” Route o”/Sales” – Renders the &lt;Sales /&gt; Component</li>

   <li>“/Sale/<strong><em>id</em></strong>” – Renders the &lt;Sale /&gt; Component with <strong>two (2)</strong> props:

    <ul>

     <li>id: The value of the <strong><em>id</em></strong> parameter from the “/Sale/<strong><em>id</em></strong>” route</li>

     <li>viewedSale: the “viewedSale” method declared in the App Class (this will be used to help us track</li>

    </ul></li>

  </ul></li>

</ul>

which sales are viewed)

<ul>

 <li>(No Route) – Renders the &lt;NotFound /&gt; Component</li>

</ul>

<h1>Step 5: “Sales” Component</h1>

The first of our two major “view” components is the “Sales” Component.  For this component to function properly, it needs to adhere to the following specification:

<ul>

 <li>We must add the following “import” statement: <strong>import { withRouter } from ‘react-router-dom’</strong> (this will help to give us access to a “history” object on this.props so that we can programmatically change routes).</li>

 <li>We must change our “export” statement to: <strong>export default withRouter(Sales);</strong></li>

 <li>Next, we must add the following components from “react-bootstrap”: { Table, Pagination }</li>

 <li>The “state” of this component must be initialized with the following values:

  <ul>

   <li>sales: [] o currentPage: 1</li>

  </ul></li>

 <li>A utility method called getData(page) must be implemented according to the following specification:

  <ul>

   <li>This function must return a <strong>promise</strong> that only resolves once the following ajax request is complete</li>

   <li>Makes an AJAX request to your “sales” API (From Assignment 1 on Heroku) route: <strong>/api/sales</strong> using the value of “page” as the “page” query parameter and “10” as the value of the “perPage” query parameter</li>

  </ul></li>

 <li>The “componentDidMount()” method must be implemented to:

  <ul>

   <li>Call our “getData(page)” method (defined above) with the value of “currentPage” (in the state) and when it is complete, update the <strong>sales </strong>value in the <strong>state </strong>with the data<strong>,</strong> causing the component to</li>

  </ul></li>

 <li>A “previousPage()” method must be implemented such that:

  <ul>

   <li>Its “this” value is correctly bound in the constructor of the “Sales” class o Any operations done in this method must only be completed if <strong>currentPage</strong> in the state is <strong>greater than 1</strong> o If the above is the case, invoke the “getData()” method with the value of (<strong>currentPage </strong>in the state <strong>– 1</strong>)</li>

   <li>Once the data returns, update the <strong>sales </strong>value in the <strong>state </strong>with the data as well as the <strong>currentPage </strong>value in the state with the value of <strong>currentPage</strong> <strong>– 1,</strong> causing the component to</li>

  </ul></li>

 <li>A “NextPage()” method must be implemented such that:

  <ul>

   <li>Its “this” value is correctly bound in the constructor of the “Sales” class o invoke the “getData()” method with the value of (<strong>currentPage </strong>in the state <strong>+ 1</strong>)</li>

   <li>Once the data returns, update the <strong>sales </strong>value in the <strong>state </strong>with the data as well as the <strong>currentPage </strong>value in the state with the value of <strong>currentPage</strong> <strong>+ 1,</strong> causing the component to</li>

  </ul></li>

 <li>Finally, we must update the render() method in the class to provide a familiar table and pagination tool to the users. This will be the same table.</li>

</ul>




To begin, copy the below render() method and replace the current one.  You will notice some comments in the code that cause the component not to render; this is just indicating where you must update the JSX code (TODO):




if(this.state.sales.length &gt; 0){

return (

&lt;div&gt;

&lt;Table hover&gt;

&lt;thead&gt;

&lt;tr&gt;

&lt;th&gt;Customer&lt;/th&gt;

&lt;th&gt;Store Location&lt;/th&gt;

&lt;th&gt;Number of Items&lt;/th&gt;

&lt;th&gt;Sale Date&lt;/th&gt;

&lt;/tr&gt;

&lt;/thead&gt;

&lt;tbody&gt;

&lt;!– TODO: Loop through the sales in the state and display their data. HINT: for the Sale date, the following code can be used: new Date(sale.saleDate).toLocaleDateString() –&gt;

&lt;/tbody&gt;

&lt;/Table&gt;

&lt;Pagination&gt;

&lt;Pagination.Prev &lt;!– TODO: invoke prevPage when this is clicked –&gt; /&gt;

&lt;Pagination.Item&gt;&lt;!– TODO: show the value of the currentPage –&gt;&lt;/Pagination.Item&gt;

&lt;Pagination.Next &lt;!– TODO: invoke nextPage when this is clicked –&gt; /&gt;             &lt;/Pagination&gt;

&lt;/div&gt;




);

}else{

return null; // NOTE: This can be changed to render a &lt;Loading /&gt; Component for a better user experience

}







<strong>IMPORTANT NOTE: To enable the user to click on a row and navigate to a specific “sale”, the following code can be used for the &lt;tr&gt; element in the above loop: </strong>

<strong> </strong>

<strong>&lt;tr key={sale._id} onClick={()=&gt;{this.props.history.push(`/Sale/${sale._id}`)}}&gt;</strong>




<h1>Step 6: “Sale” Component</h1>

The second of our two major “view” components is the “Sale” Component.  For this component to function properly, it needs to adhere to the following specification:




<ul>

 <li>First, we must add the following components from “react-bootstrap”: { ListGroup, ListGroupItem, Table }</li>

 <li>Next, the “state” of this component must be initialized with the following value:</li>

</ul>

o sale: {} o loading: true

<ul>

 <li>The “componentDidMount()” method must be implemented to:</li>

</ul>

o Make an AJAX request to your “sales” API (From Assignment 1 on Heroku) route: <strong>/api/sale/id</strong> using the value of “id” passed in “props” as the “id” route parameter.  When it is complete:

<ul>

 <li>Check to see if the data contains an _id value and if it does, invoke the <strong>viewedSale(id)</strong> method sent to this component in its <strong>props</strong> during routing with the _id value. This should place this id in the “Previously Viewed” drop down list</li>

 <li>Next, update the sale value in the state with the data, causing the component to render.</li>

</ul>

<ul>

 <li>The “componentDidUpdate(prevProps)” method must be implemented to:

  <ul>

   <li>Compare prevProps.id and this.props.id to see if they are different, ie:</li>

  </ul></li>

</ul>

if (prevProps.id !== this.props.id) { … }

<ul>

 <li>If they are indeed different (indicating that a different product should be viewed), set the “loading” property in the state to <strong>true</strong> (causing the component to <strong>render</strong>) and then perform the same tasks as the “componentDidMount()” method (above), ie: perform another AJAX request and update the “state”.</li>

</ul>

<ul>

 <li>Before we move on to the “render()” method, we should also define a utility function called itemTotal(items) which simply takes an array of item objects (ie: the items in the current sale) and calculates the sale total using the same formula that was used in Assignment 2</li>

 <li>Finally, we must update the render() method in the class to show relevant “Sale” data to the user (specifically the customer information).</li>

</ul>




To begin, copy the below render() method and replace the current one.  You will notice some comments in the code that cause the component not to render; this is just indicating where you must update the JSX code (TODO):




if (this.state.loading) {     return null; // NOTE: This can be changed to render a &lt;Loading /&gt; Component for a better user experience

} else {

if (this.state.sale._id) {         return (&lt;div&gt;

&lt;h1&gt;Sale: &lt;!– TODO: Show the Sale ID –&gt;&lt;/h1&gt;

&lt;h2&gt;Customer&lt;/h2&gt;




&lt;ListGroup&gt;

&lt;ListGroupItem&gt;&lt;strong&gt;email:&lt;/strong&gt; &lt;!– TODO: Show the Customer Email –&gt;&lt;/ListGroupItem&gt;

&lt;ListGroupItem&gt;&lt;strong&gt;age:&lt;/strong&gt; &lt;!– TODO: Show the Customer Age –&gt;&lt;/ListGroupItem&gt;

&lt;ListGroupItem&gt;&lt;strong&gt;satisfaction:&lt;/strong&gt; &lt;!– TODO: Show the Customer Satisfaction –&gt; / 5&lt;/ListGroupItem&gt;

&lt;/ListGroup&gt;




&lt;h2&gt; Items: &lt;!– TODO: Show the Item Total –&gt;&lt;/h2&gt;




&lt;Table&gt;

&lt;thead&gt;

&lt;tr&gt;

&lt;th&gt;Product Name&lt;/th&gt;

&lt;th&gt;Quantity&lt;/th&gt;

&lt;th&gt;Price&lt;/th&gt;

&lt;/tr&gt;

&lt;/thead&gt;                 &lt;tbody&gt;

&lt;!– TODO: loop through all of the sale items and display their data –&gt;                 &lt;/tbody&gt;

&lt;/Table&gt;

&lt;/div&gt;);

} else {

return &lt;div&gt;&lt;h1&gt;Unable to find Sale&lt;/h1&gt;&lt;p&gt;id: {this.props.id}&lt;/p&gt;&lt;/div&gt;

}

}




Once you have updated this final component, your assignment should be complete.  Please check it against the sample video (top) and ensure that its functioning correctly before submitting.