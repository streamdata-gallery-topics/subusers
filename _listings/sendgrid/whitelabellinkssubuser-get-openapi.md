---
swagger: "2.0"
x-collection-name: SendGrid
x-complete: 0
info:
  title: SendGrid Get Whitelabel Links Subuser
  description: |-
    **This endpoint allows you to retrieve the associated link whitelabel for a subuser.**

    Link whitelables can be associated with subusers from the parent account. This functionality allows
    subusers to send mail using their parent's linke whitelabels. To associate a link whitelabel, the parent account
    must first create a whitelabel and validate it. The parent may then associate that whitelabel with a subuser via the API or the Subuser Management page in the user interface.

    Email link whitelabels allow all of the click-tracked links you send in your emails to include the URL of your domain instead of sendgrid.net.

    For more information, please see our [User Guide](https://sendgrid.com/docs/API_Reference/Web_API_v3/Whitelabel/links.html).
  version: 1.0.0
host: api.sendgrid.com
basePath: /v3
schemes:
- http
produces:
- application/json
consumes:
- application/json
paths:
  /subusers:
    get:
      summary: Get Subusers
      description: |-
        This endpoint allows you to retrieve a list of all of your subusers. You can choose to retrieve specific subusers as well as limit the results that come back from the API.

        For more information about Subusers:

        * [User Guide > Subusers](https://sendgrid.com/docs/User_Guide/Settings/Subusers/index.html)
        * [Classroom > How do I add more subusers to my account?](https://sendgrid.com/docs/Classroom/Basics/Account/how_do_i_add_more_subusers_to_my_account.html)
      operationId: GET_subusers
      x-api-path-slug: subusers-get
      parameters:
      - in: query
        name: limit
        description: The number of results you would like to get in each request
      - in: query
        name: offset
        description: The number of subusers to skip
      - in: query
        name: username
        description: The username of this subuser
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
    post:
      summary: Add Subusers
      description: |-
        This endpoint allows you to retrieve a list of all of your subusers. You can choose to retrieve specific subusers as well as limit the results that come back from the API.

        For more information about Subusers:

        * [User Guide > Subusers](https://sendgrid.com/docs/User_Guide/Settings/Subusers/index.html)
        * [Classroom > How do I add more subusers to my account?](https://sendgrid.com/docs/Classroom/Basics/Account/how_do_i_add_more_subusers_to_my_account.html)
      operationId: POST_subusers
      x-api-path-slug: subusers-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
  /subusers/reputations:
    get:
      summary: Get Subusers Reputations
      description: |-
        Subuser sender reputations give a good idea how well a sender is doing with regards to how recipients and recipient servers react to the mail that is being received. When a bounce, spam report, or other negative action happens on a sent email, it will effect your sender rating.

        This endpoint allows you to request the reputations for your subusers.
      operationId: subusers.reputations.get
      x-api-path-slug: subusersreputations-get
      parameters:
      - in: query
        name: usernames
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Reputations
  /subusers/stats:
    get:
      summary: Get Subusers Stats
      description: |-
        **This endpoint allows you to retrieve the email statistics for the given subusers.**

        You may retrieve statistics for up to 10 different subusers by including an additional _subusers_ parameter for each additional subuser.

        While you can always view the statistics for all email activity on your account, subuser statistics enable you to view specific segments of your stats. Emails sent, bounces, and spam reports are always tracked for subusers. Unsubscribes, clicks, and opens are tracked if you have enabled the required settings.

        For more information, see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/subuser.html).
      operationId: subusers.stats.get
      x-api-path-slug: subusersstats-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the statistics
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: Limits the number of results returned per page
      - in: query
        name: offset
        description: The point in the list to begin retrieving results from
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      - in: query
        name: subusers
        description: The subuser you want to retrieve statistics for
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Stats
  /subusers/stats/monthly:
    get:
      summary: Get Subusers Stats Monthly
      description: |-
        **This endpoint allows you to retrieve the monthly email statistics for all subusers over the given date range.**

        While you can always view the statistics for all email activity on your account, subuser statistics enable you to view specific segments of your stats for your subusers. Emails sent, bounces, and spam reports are always tracked for subusers. Unsubscribes, clicks, and opens are tracked if you have enabled the required settings.

        When using the `sort_by_metric` to sort your stats by a specific metric, you can not sort by the following metrics:
        `bounce_drops`, `deferred`, `invalid_emails`, `processed`, `spam_report_drops`, `spam_reports`, or `unsubscribe_drops`.

        For more information, see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/subuser.html).
      operationId: subusers.stats.monthly.get
      x-api-path-slug: subusersstatsmonthly-get
      parameters:
      - in: query
        name: date
        description: The date of the month to retrieve statistics for
      - in: query
        name: limit
        description: Optional field to limit the number of results returned
      - in: query
        name: offset
        description: Optional beginning point in the list to retrieve from
      - in: query
        name: sort_by_direction
        description: The direction you want to sort
      - in: query
        name: sort_by_metric
        description: The metric that you want to sort by
      - in: query
        name: subuser
        description: A substring search of your subusers
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Stats
      - Monthly
  /subusers/stats/sums:
    get:
      summary: Get Subusers Stats Sums
      description: |-
        **This endpoint allows you to retrieve the total sums of each email statistic metric for all subusers over the given date range.**


        While you can always view the statistics for all email activity on your account, subuser statistics enable you to view specific segments of your stats. Emails sent, bounces, and spam reports are always tracked for subusers. Unsubscribes, clicks, and opens are tracked if you have enabled the required settings.

        For more information, see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/subuser.html).
      operationId: subusers.stats.sums.get
      x-api-path-slug: subusersstatssums-get
      parameters:
      - in: query
        name: aggregated_by
        description: How to group the statistics
      - in: query
        name: end_date
        description: The end date of the statistics to retrieve
      - in: query
        name: limit
        description: Limits the number of results returned per page
      - in: query
        name: offset
        description: The point in the list to begin retrieving results from
      - in: query
        name: sort_by_direction
        description: The direction you want to sort
      - in: query
        name: sort_by_metric
        description: The metric that you want to sort by
      - in: query
        name: start_date
        description: The starting date of the statistics to retrieve
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Stats
      - Sums
  /subusers/{subuser_name}:
    delete:
      summary: Delete Subusers Subuser Name
      description: |-
        This endpoint allows you to delete a subuser. This is a permanent action, once deleted a subuser cannot be retrieved.

        For more information about Subusers:

        * [User Guide > Subusers](https://sendgrid.com/docs/User_Guide/Settings/Subusers/index.html)
        * [Classroom > How do I add more subusers to my account?](https://sendgrid.com/docs/Classroom/Basics/Account/how_do_i_add_more_subusers_to_my_account.html)
      operationId: subusers.subuser_name.delete
      x-api-path-slug: subuserssubuser-name-delete
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
    patch:
      summary: Patch Subusers Subuser Name
      description: |-
        This endpoint allows you to enable or disable a subuser.

        For more information about Subusers:

        * [User Guide > Subusers](https://sendgrid.com/docs/User_Guide/Settings/Subusers/index.html)
        * [Classroom > How do I add more subusers to my account?](https://sendgrid.com/docs/Classroom/Basics/Account/how_do_i_add_more_subusers_to_my_account.html)
      operationId: subusers.subuser_name.patch
      x-api-path-slug: subuserssubuser-name-patch
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
  /subusers/{subuser_name}/ips:
    put:
      summary: Put Subusers Subuser Name Ips
      description: "Each subuser should be assigned to an IP address, from which all
        of this subuser's mail will be sent. Often, this is the same IP as the parent
        account, but each subuser can have their own, or multiple, IP addresses as
        well. \n\nMore information:\n\n* [How to request more IPs](https://sendgrid.com/docs/Classroom/Basics/Account/adding_an_additional_dedicated_ip_to_your_account.html)\n*
        [IPs can be whitelabeled](https://sendgrid.com/docs/User_Guide/Settings/Whitelabel/ips.html)"
      operationId: subusers.subuser_name.ips.put
      x-api-path-slug: subuserssubuser-nameips-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Ips
  /subusers/{subuser_name}/monitor:
    delete:
      summary: Delete Subusers Subuser Name Monitor
      description: Subuser monitor settings allow you to receive a sample of an outgoing
        message by a specific customer at a specific frequency of emails.
      operationId: subusers.subuser_name.monitor.delete
      x-api-path-slug: subuserssubuser-namemonitor-delete
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Monitor
    get:
      summary: Get Subusers Subuser Name Monitor
      description: Subuser monitor settings allow you to receive a sample of an outgoing
        message by a specific customer at a specific frequency of emails.
      operationId: subusers.subuser_name.monitor.get
      x-api-path-slug: subuserssubuser-namemonitor-get
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Monitor
    post:
      summary: Add Subusers Subuser Name Monitor
      description: Subuser monitor settings allow you to receive a sample of an outgoing
        message by a specific customer at a specific frequency of emails.
      operationId: subusers.subuser_name.monitor.post
      x-api-path-slug: subuserssubuser-namemonitor-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Monitor
    put:
      summary: Put Subusers Subuser Name Monitor
      description: Subuser monitor settings allow you to receive a sample of an outgoing
        message by a specific customer at a specific frequency of emails.
      operationId: subusers.subuser_name.monitor.put
      x-api-path-slug: subuserssubuser-namemonitor-put
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Monitor
  /subusers/{subuser_name}/stats/monthly:
    get:
      summary: Get Subusers Subuser Name Stats Monthly
      description: |-
        **This endpoint allows you to retrive the monthly email statistics for a specific subuser.**

        While you can always view the statistics for all email activity on your account, subuser statistics enable you to view specific segments of your stats for your subusers. Emails sent, bounces, and spam reports are always tracked for subusers. Unsubscribes, clicks, and opens are tracked if you have enabled the required settings.

        When using the `sort_by_metric` to sort your stats by a specific metric, you can not sort by the following metrics:
        `bounce_drops`, `deferred`, `invalid_emails`, `processed`, `spam_report_drops`, `spam_reports`, or `unsubscribe_drops`.

        For more information, see our [User Guide](https://sendgrid.com/docs/User_Guide/Statistics/subuser.html).
      operationId: subusers.subuser_name.stats.monthly.get
      x-api-path-slug: subuserssubuser-namestatsmonthly-get
      parameters:
      - in: query
        name: date
        description: The date of the month to retrieve statistics for
      - in: query
        name: limit
        description: Optional field to limit the number of results returned
      - in: query
        name: offset
        description: Optional beginning point in the list to retrieve from
      - in: query
        name: sort_by_direction
        description: The direction you want to sort
      - in: query
        name: sort_by_metric
        description: The metric that you want to sort by
      responses:
        200:
          description: OK
      tags:
      - Email
      - Subusers
      - Subuser
      - Name
      - Stats
      - Monthly
  /whitelabel/domains/subuser:
    delete:
      summary: Delete Whitelabel Domains Subuser
      description: |-
        **This endpoint allows you to disassociate a specific whitelabel from a subuser.**

        A domain whitelabel allows you to remove the ???via??? or ???sent on behalf of??? message that your recipients see when they read your emails. Whitelabeling a domain allows you to replace sendgrid.net with your personal sending domain. You will be required to create a subdomain so that SendGrid can generate the DNS records which you must give to your host provider. If you choose to use Automated Security, SendGrid will provide you with 3 CNAME records. If you turn Automated Security off, you will be given 2 TXT records and 1 MX record.

        Domain whitelabels can be associated with (i.e. assigned to) subusers from a parent account. This functionality allows subusers to send mail using their parent's whitelabels. To associate a whitelabel with a subuser, the parent account must first create the whitelabel and validate it. The the parent may then associate the whitelabel via the subuser management tools.

        For more information on whitelabeling, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Settings/Whitelabel/index.html)

        ## URI Parameters
        | URI Parameter   | Type  | Required?  | Description  |
        |---|---|---|---|
        | username | string  | required  | Username for the subuser to find associated whitelabels for. |
      operationId: whitelabel.domains.subuser.delete
      x-api-path-slug: whitelabeldomainssubuser-delete
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Domains
      - Subuser
    get:
      summary: Get Whitelabel Domains Subuser
      description: |-
        **This endpoint allows you to retrieve all of the whitelabels that have been assigned to a specific subuser.**

        A domain whitelabel allows you to remove the ???via??? or ???sent on behalf of??? message that your recipients see when they read your emails. Whitelabeling a domain allows you to replace sendgrid.net with your personal sending domain. You will be required to create a subdomain so that SendGrid can generate the DNS records which you must give to your host provider. If you choose to use Automated Security, SendGrid will provide you with 3 CNAME records. If you turn Automated Security off, you will be given 2 TXT records and 1 MX record.

        Domain whitelabels can be associated with (i.e. assigned to) subusers from a parent account. This functionality allows subusers to send mail using their parent's whitelabels. To associate a whitelabel with a subuser, the parent account must first create the whitelabel and validate it. The the parent may then associate the whitelabel via the subuser management tools.

        For more information on whitelabeling, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Settings/Whitelabel/index.html)

        ## URI Parameters
        | URI Parameter   | Type  | Description  |
        |---|---|---|
        | username | string  | Username of the subuser to find associated whitelabels for. |
      operationId: whitelabel.domains.subuser.get
      x-api-path-slug: whitelabeldomainssubuser-get
      parameters:
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Domains
      - Subuser
  /whitelabel/domains/{domain_id}/subuser:
    post:
      summary: Add Whitelabel Domains Domain  Subuser
      description: |-
        **This endpoint allows you to associate a specific domain whitelabel with a subuser.**

        A domain whitelabel allows you to remove the ???via??? or ???sent on behalf of??? message that your recipients see when they read your emails. Whitelabeling a domain allows you to replace sendgrid.net with your personal sending domain. You will be required to create a subdomain so that SendGrid can generate the DNS records which you must give to your host provider. If you choose to use Automated Security, SendGrid will provide you with 3 CNAME records. If you turn Automated Security off, you will be given 2 TXT records and 1 MX record.

        Domain whitelabels can be associated with (i.e. assigned to) subusers from a parent account. This functionality allows subusers to send mail using their parent's whitelabels. To associate a whitelabel with a subuser, the parent account must first create the whitelabel and validate it. The the parent may then associate the whitelabel via the subuser management tools.

        For more information on whitelabeling, please see our [User Guide](https://sendgrid.com/docs/User_Guide/Settings/Whitelabel/index.html)

        ## URI Parameters
        | URI Parameter   | Type   | Description  |
        |---|---|---|
        | domain_id | integer   | ID of the domain whitelabel to associate with the subuser. |
      operationId: whitelabel.domains.domain_id.subuser.post
      x-api-path-slug: whitelabeldomainsdomain-idsubuser-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Domains
      - Domain
      - ""
      - Subuser
  /whitelabel/links/subuser:
    delete:
      summary: Delete Whitelabel Links Subuser
      description: |-
        **This endpoint allows you to disassociate a link whitelabel from a subuser.**

        Link whitelables can be associated with subusers from the parent account. This functionality allows
        subusers to send mail using their parent's linke whitelabels. To associate a link whitelabel, the parent account
        must first create a whitelabel and validate it. The parent may then associate that whitelabel with a subuser via the API or the Subuser Management page in the user interface.

        Email link whitelabels allow all of the click-tracked links you send in your emails to include the URL of your domain instead of sendgrid.net.

        For more information, please see our [User Guide](https://sendgrid.com/docs/API_Reference/Web_API_v3/Whitelabel/links.html).
      operationId: whitelabel.links.subuser.delete
      x-api-path-slug: whitelabellinkssubuser-delete
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      - in: query
        name: username
        description: The username of the subuser account that you want to disassociate
          a link whitelabel from
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Links
      - Subuser
    get:
      summary: Get Whitelabel Links Subuser
      description: |-
        **This endpoint allows you to retrieve the associated link whitelabel for a subuser.**

        Link whitelables can be associated with subusers from the parent account. This functionality allows
        subusers to send mail using their parent's linke whitelabels. To associate a link whitelabel, the parent account
        must first create a whitelabel and validate it. The parent may then associate that whitelabel with a subuser via the API or the Subuser Management page in the user interface.

        Email link whitelabels allow all of the click-tracked links you send in your emails to include the URL of your domain instead of sendgrid.net.

        For more information, please see our [User Guide](https://sendgrid.com/docs/API_Reference/Web_API_v3/Whitelabel/links.html).
      operationId: whitelabel.links.subuser.get
      x-api-path-slug: whitelabellinkssubuser-get
      parameters:
      - in: query
        name: No Name
      - in: query
        name: username
        description: The username of the subuser to retrieve associated link whitelabels
          for
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Links
      - Subuser
  /whitelabel/links/{link_id}/subuser:
    post:
      summary: Add Whitelabel Links Link  Subuser
      description: |-
        **This endpoint allows you to associate a link whitelabel with a subuser account.**

        Link whitelables can be associated with subusers from the parent account. This functionality allows
        subusers to send mail using their parent's linke whitelabels. To associate a link whitelabel, the parent account
        must first create a whitelabel and validate it. The parent may then associate that whitelabel with a subuser via the API or the Subuser Management page in the user interface.

        Email link whitelabels allow all of the click-tracked links you send in your emails to include the URL of your domain instead of sendgrid.net.

        For more information, please see our [User Guide](https://sendgrid.com/docs/API_Reference/Web_API_v3/Whitelabel/links.html).
      operationId: whitelabel.links.link_id.subuser.post
      x-api-path-slug: whitelabellinkslink-idsubuser-post
      parameters:
      - in: body
        name: body
        schema:
          $ref: '#/definitions/holder'
      - in: query
        name: No Name
      responses:
        200:
          description: OK
      tags:
      - Email
      - Whitelabel
      - Links
      - Link
      - ""
      - Subuser
x-streamrank:
  polling_total_time_average: 0
  polling_size_download_average: 0
  streaming_total_time_average: 0
  streaming_size_download_average: 0
  change_yes: 0
  change_no: 0
  time_percentage: 0
  size_percentage: 0
  change_percentage: 0
  last_run: ""
  days_run: 0
  minute_run: 0
---