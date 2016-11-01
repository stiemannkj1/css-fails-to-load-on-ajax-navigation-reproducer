# [JAVASERVERFACES-4195](https://java.net/jira/browse/JAVASERVERFACES-4195) Reproducer

This project is a reproducer for [JAVASERVERFACES-4195](https://java.net/jira/browse/JAVASERVERFACES-4195): CSS fails to load on ajax navigation.

## Steps to reproduce:

1. Clone the project:

        git clone https://github.com/stiemannkj1/css-fails-to-load-on-ajax-navigation-reproducer.git

2. Build the project with maven. You can use the `myfaces` profile to use myfaces instead of mojarra (for example: `-P myfaces`). You can use the `jsf.version` property to change the version of JSF being used (for example: `-Djsf.verison=2.3.0-m06`).

        cd css-fails-to-load-on-ajax-navigation-reproducer && mvn clean install

3. Deploy the project to tomcat:

        cp target/css-fails-to-load-on-ajax-navigation-reproducer*.war $TOMCAT_HOME/webapps/

4. Navigate to **`index.faces`** in the browser:

      [http://localhost:8080/css-fails-to-load-on-ajax-navigation-reproducer-1.0-SNAPSHOT/index.faces](http://localhost:8080/css-fails-to-load-on-ajax-navigation-reproducer-1.0-SNAPSHOT/index.faces)

5. Click the *page2* button.

6. Note that an alert with the text "example.js resource loaded" appears confirming that javascript resources have been loaded for the ajax navigation.

If the bug still exists, the background color will not change or appear red.

If the bug is fixed, the background will appear red due to CSS styles applied to the `<body>` element by **`example.css`**.

**Note:** This works correctly in Myfaces. You can test myfaces by rebuilding the project with  `mvn clean install -P myfaces` and following the steps above.

**Note 2:** The CSS is rendered correctly in the partial response, however it is not added to the `<head>` section correctly.
