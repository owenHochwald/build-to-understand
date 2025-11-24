# Build to Understand

> **Find your coding ikigai.** Build projects at the intersection of what you're learning in class, what interests you personally, and what companies actually hire for.

---

You aced Data Structures. You understood Concurrency in OS. You can explain how to reverse a linked list.

But when you open a job description asking for "experience with Redis, Docker, GraphQL, and distributed systems," you freeze.

Coursework teaches theory. Jobs demand production experience. For those not lucky enough to get internship experience in these areas, most students fill the gap with hackathon projects that look good for 48 hours but teach nothing lasting.

Start building at the **intersection of three circles**:

1. **What you just learned in class** -> Solidify theory through application
2. **What job descriptions ask for** -> Build resume-worthy skills  
3. **What actually interests you** -> Stay motivated past a single weekend

**Each project in this guide is designed to be semester-long.** This isn't a weekend hackathon list—these are substantial projects that teach production-grade skills through sustained effort.

---

## Build for Demos

**The golden rule: If you can't demo it and measure it, you didn't build it.**

Every project in this roadmap is designed to be:
- **Demoable**: Show it to recruiters, TAs, friends. Screen recordings, live deployments, GitHub READMEs with screenshots.
- **Measurable**: "I built a chat app"   -> "I built a chat app handling 10k concurrent connections with p95 latency under 100ms"

---

## "But Someone Already Built This..."

**Good. Build it anyway.**

Seen a URL shortener before? Build yours with better caching strategies.  
Seen a task queue? Build yours with custom scheduling algorithms.  
Seen a chat app? Build yours with better scalability patterns.

Every rebuild teaches you:
- **What makes the original design choices smart** (or not)
- **Where you can improve** performance, architecture, or UX
- **How to make production-grade decisions** yourself

**Your version doesn't need to be revolutionary. It needs to be yours.**

---

## Understanding the Levels

### **Level 1: Make it work**
- **Focus**: Core functionality only
- **Tech**: Whatever you know best
- **Goal**: Can demo the basic feature

### **Level 2: Make it real**
- **Focus**: Handle edge cases, add polish, deploy it
- **Tech**: Add 1-2 production patterns
- **Goal**: You'd actually use this, it's live on the internet

### **Level 3: Make it yours**
- **Focus**: One interesting challenge you choose
- **Tech**: Whatever solves YOUR problem
- **Goal**: Learn something new that interests you, measure what you built

---

## Projects by Course

### Object-Oriented Programming (OOP)

> **What you learned:** Classes, inheritance, polymorphism, SOLID principles, design patterns, dependency injection, interfaces/abstract classes

---

#### **LeetCode Progress Tracker with Analytics**

**Synergy / Why build this:** You're already grinding LeetCode for interviews, why not build a system to organize your progress while learning OOP design patterns, REST APIs, and database design? This teaches you how to model real-world relationships (problems, submissions, patterns) with proper OOP architecture.

**Job skills:** `rest-api` `database-design` `oop-patterns` `backend-language` `testing`  
**Coursework:** `oop-principles` `solid` `design-patterns` `database-design`

---

**Level 1: Make it work** 
- Track problems you've solved: add, view, search
- Store: problem name, difficulty, date attempted, your notes
- Design basic classes: `Problem`, `Submission`, `Topic`
- **Tech**: Your favorite backend language + any database (SQLite is fine to start)
- **Demo**: "Show me all Medium problems I solved this week"

**Level 2: Make it real** 
- Apply OOP patterns where they naturally fit:
  - Different problem-solving approaches (Greedy, DP, Two Pointer)  -> Strategy Pattern
  - Different problem types (Array, Tree, Graph)  -> Inheritance
- Track: problem attempts, time spent, patterns used
- Handle: What if you attempt a problem multiple times? How do you store that?
- Add authentication (JWT or sessions)
- **Database**: Use a relational database (Postgres, MySQL) or hosted option (Supabase, PlanetScale)
- Write unit tests for your core logic
- **Hosting**: Deploy your API (Render, Railway, Fly.io, or AWS free tier)
- **Demo**: Use this for your actual interview prep, shareable link

**Level 3: Make it yours**

Pick ONE challenge:
- **How would you recommend problems?** Build a system that suggests "based on what you've solved, try these next"
- **What patterns are you weak at?** Generate study plans targeting your weak areas
- **Can you predict interview readiness?** Design a scoring system based on problem coverage and success rate
- **What if 1000 students used this?** Add caching, optimize queries, handle concurrent updates

**Measure what you built:**
- API response times (use Postman, curl, or simple logging)
- Database query performance (use `EXPLAIN` in SQL)
- Test coverage percentage (Jest, pytest, Go's built-in testing)

---

#### **Expense Splitting App (Splitwise Clone)**

**Synergy / Why build this:** Ever split a dinner bill and wondered "who owes whom?" This problem is deceptively complex, it's really a graph problem disguised as a finance app. You'll learn to model many-to-many relationships, handle concurrent transactions safely, and implement actual algorithms (debt simplification is a graph minimization problem).

**Job skills:** `database-transactions` `graph-algorithms` `rest-api` `backend-language` `data-modeling`  
**Coursework:** `database-design` `transactions` `acid-properties` `graph-algorithms`

---

**Level 1: Make it work** 
- Create groups, add expenses, split between people
- Basic calculation: "Alice paid 30, split 3 ways -> Bob owes 10, Carol owes 10"
- Store: Groups, Users, Expenses, who paid, who owes
- **Tech**: Any backend language + database (even JSON files work initially)
- **Demo**: "I created a group, added an expense, see who owes what"

**Level 2: Make it real** 
- Handle complex splits: unequal amounts, percentages, "Alice pays for herself + Bob"
- Implement database transactions: creating an expense must atomically update all balances
- Add proper foreign keys and constraints (prevent negative amounts, deleted users, etc.)
- Implement debt simplification: minimize number of transactions needed to settle up
  - This is a graph problem: nodes are people, edges are debts
  - Basic algorithm: find cycles and collapse them
- **Database**: Relational database required (Postgres, MySQL) for transaction support
- Add authentication and group permissions
- **Hosting**: Deploy (Render, Railway, Fly.io, or cloud platform)
- **Demo**: Live app where you can actually split bills with friends

**Level 3: Make it yours** 

Pick ONE challenge:
- **How do you handle concurrent expense additions?** What if two people add expenses simultaneously? Explore database locking
- **Can you optimize the debt graph further?** Research graph algorithms for minimizing transactions (it's NP-complete!)
- **What about multiple currencies?** Add currency conversion with historical rates
- **How would you handle disputes?** Design a system for "Alice says she paid, Bob disagrees"


**Measure what you built:**
- Transaction processing time (milliseconds per expense creation)
- Debt graph complexity: before simplification (N edges) vs after (M edges)
- Database query performance for "show me all balances in this group"
- Correctness: total debt should always sum to zero

---

### Databases

> **What you learned:** Schema design, normalization, indexes, transactions, ACID properties, query optimization, joins

---

#### **Course Review Platform with Advanced Search**

**Synergy / Why build this:** You wish this existed at your university, a place to find real reviews before registering. This teaches database normalization (how do you model courses, professors, reviews without duplication?), indexing (fast search is crucial), and full-text search (searching through review text efficiently).

**Job skills:** `database-indexing` `full-text-search` `query-optimization` `rest-api` `backend-language`  
**Coursework:** `normalization` `indexing` `query-optimization` `transactions`

---

**Level 1: Make it work** 
- Add and view course reviews
- Store: Course name, professor, rating (1-5), review text, date
- Basic search: find reviews by course name
- **Tech**: Your favorite backend language + any database
- **Demo**: "Search for CPSC 213, see all reviews"

**Level 2: Make it real** 
- Design normalized schema: separate tables for Courses, Professors, Reviews, Users
  - Why? One professor teaches multiple courses, avoid duplicating professor info
- Add foreign keys and referential integrity
- Create indexes on frequently queried columns (course_id, professor_id, created_at)
- Implement full-text search for review content
- Add aggregated stats: average rating per course, review count
- Handle: What if someone submits duplicate reviews? Edit/delete reviews?
- **Database**: Relational database with full-text search support (Postgres recommended)
- **Hosting**: Deploy your API + database (Render with Postgres, or Supabase, or cloud platform)
- **Demo**: Fast search through review text, filter by rating/professor

**Level 3: Make it yours** 

Pick ONE challenge:
- **How fast can you make search?** Use `EXPLAIN ANALYZE` to optimize slow queries, experiment with different index strategies
- **Can you add faceted search?** Filter by: professor AND semester AND difficulty simultaneously
- **What about pagination?** Research cursor-based vs offset-based pagination for large datasets
- **How do you handle search relevance?** Should older reviews rank lower? Should highly-rated reviews appear first?

**Questions to explore:**
- How do real platforms like RateMyProfessor rank search results?
- How would you prevent review bombing?
---

#### **University Course Prerequisite Mapper (DSA / Databases)**

**Synergy / Why build this:** You're frustrated trying to plan your degree, which courses can you actually take next semester? This is a graph problem with hierarchical data (prerequisites are a directed acyclic graph... unless your university has circular prerequisites!). You'll learn recursive queries, cycle detection, and graph algorithms. Companies need engineers who can model complex relationships and traverse them efficiently.

**Job skills:** `graph-algorithms` `recursive-queries` `database-design` `backend-language` `data-visualization`  
**Coursework:** `graph-algorithms` `recursive-queries` `foreign-keys` `database-constraints`

---

**Level 1: Make it work** 
- Store courses and their prerequisites
- Basic queries: "What are the prerequisites for CPSC 313?" "What courses can I take if I've completed CPSC 110 and 121?"
- Store: Course code, name, credits, prerequisites (list of course codes)
- **Tech**: Any backend language + database (SQLite works)
- **Demo**: "Show me all prerequisites for a senior-level course"

**Level 2: Make it real** 
- Design proper schema: self-referencing table (Prerequisite table with course_id and prereq_id)
- Implement recursive queries to find ALL prerequisites (not just direct ones)
  - Would be some good practice implementing graph traversal in code!
- Add cycle detection: prevent "Course A requires Course B requires Course A"
- Add course offerings: which terms is each course offered? (Fall/Spring/Summer)
- Generate valid course sequences: "What order should I take these courses?"
- **Database**: Any SQL database (recursive CTEs are standard SQL)
- **Hosting**: Deploy your API + database
- **Demo**: Given your completed courses, show what you can take next semester

**Level 3: Make it yours** 

Pick ONE challenge:
- **Can you visualize the prerequisite graph?** Export to GraphViz or build an interactive visualization (D3.js, vis.js)
- **What about "recommended" vs "required" prerequisites?** Model soft dependencies
- **Can you detect which courses are bottlenecks?** Find courses that block the most other courses

**Measure what you built:**
- Recursive query performance: time to find all prerequisites for deepest course
- Graph traversal speed: nodes visited, cycles detected
- Plan generation time: seconds to generate 4-year plan
---

### Computer Networks

> **What you learned:** TCP/IP, HTTP, sockets, DNS, protocols, OSI model, network programming

---

#### **Real-Time Study Group Chat with Persistent History**

**Synergy / Why build this:** HTTP is request-response, but chat is continuous. This teaches you persistent connections (WebSockets), the difference between polling and push, and how to scale real-time systems.

**Job skills:** `websockets` `real-time-systems` `caching` `backend-language` `database-design`  
**Coursework:** `tcp-ip` `persistent-connections` `network-protocols` `concurrency`

---

**Level 1: Make it work** 
- Implement WebSocket server that accepts connections
- Users can send messages, messages broadcast to all users in a room
- In-memory storage (messages lost on restart)
- Simple frontend: HTML + JavaScript WebSocket API
- **Tech**: Any backend language with WebSocket support (Node.js/ws, Go/gorilla, Python/websockets)
- **Demo**: Open two browser tabs, type in one, see it appear in the other instantly

**Level 2: Make it real** 
- Persist message history to a database
- Handle connection lifecycle properly: connect, disconnect, reconnect
- Add user authentication (JWT tokens for WebSocket connections)
- Implement "user is typing" indicators and online presence
- Add multiple rooms/channels
- Handle edge cases: What if connection drops? Reconnection with message replay
- **Database**: Any database (Postgres for relational, MongoDB for document-based)
- Add rate limiting per connection (prevent spam)
- **Hosting**: Deploy your WebSocket server (Render, Railway, Fly.io—ensure WebSocket support)
- **Demo**: Real deployed chat that persists history, handles reconnections gracefully

**Level 3: Make it yours** 

Pick ONE challenge:
- **How many concurrent connections can you handle?** K6 / Volt load testing!
- **What about message delivery guarantees?** Implement "at-least-once" delivery with acknowledgments
- **How would you add read receipts?** Track who has read which messages

**Measure what you built:**
- Message latency: time from send to receive (p50, p95, p99)
- Memory usage per connection
---

#### **Smart URL Shortener with Analytics**

**Synergy / Why build this:** A URL shortener really ties into how real systems works (caching headers, database lookups, and scaling patterns). Plus, adding analytics (click tracking, referrer info) shows you can build data-driven features.

**Job skills:** `http-protocol` `caching-strategies` `rest-api` `backend-language` `analytics`  
**Coursework:** `http` `status-codes` `caching` `database-design`

---

**Level 1: Make it work**
- Submit a long URL  -> get back a short code (e.g., "abc123")
- Visit short URL  -> 301/302 redirect to original URL
- Store mappings in any database
- Generate short codes (base62 encoding, or random strings)
- **Tech**: Any backend language + any database
- **Demo**: "bit.ly/xyz now goes to my-super-long-url.com"

**Level 2: Make it real** 
- Understand HTTP redirects: 301 (permanent) vs 302 (temporary)—which should you use and why?
- Add basic analytics: count clicks per link, timestamp each click
- Add custom short codes: users can request "bit.ly/myname" if available
- Implement caching for hot URLs (in-memory cache or Redis)
  - Most traffic hits a small % of links—caching avoids repeated DB lookups
- Rate limiting to prevent abuse
- **Database**: Relational (Postgres, MySQL) or NoSQL (MongoDB, DynamoDB)
- **Optional caching**: Redis or in-memory cache (start simple, add if needed)
- **Hosting**: Deploy your API (Render, Railway, cloud platform)
- **Demo**: Live shortener with analytics dashboard showing click counts

**Level 3: Make it yours** 

Pick ONE challenge:
- **How would you scale to 1M links and 100k requests/second?** 
- **What if you run out of short codes?** Calculate: with 6 characters (base62), how many URLs can you store?

**Measure what you built:**
- Redirect latency: time from request to redirect 
- Cache hit rate: percentage of requests served from cache vs database
- Throughput: requests per second your server can handle

---

### Operating Systems

> **What you learned:** Processes, threads, concurrency, synchronization, memory management, scheduling, deadlocks

---

#### **Task Scheduler with Priority Queues & Worker Pools**

**Synergy / Why build this:** Every production system needs background job processing, sending emails, processing images, generating reports. This teaches you the OS concepts you just learned (threads, scheduling algorithms, synchronization) in a practical context.

**Job skills:** `concurrency` `message-queues` `scheduling-algorithms` `backend-language` `distributed-systems`  
**Coursework:** `scheduling-algorithms` `threads` `synchronization` `concurrency`

---

**Level 1: Make it work** 
- Accept tasks via API: task name, priority, payload, task duration
- Store tasks in a queue (in-memory to start)
- Create a worker pool (fixed number of threads/goroutines) that processes tasks
- Support simple scheduling: FIFO (first-in-first-out) or priority-based
- **Tech**: Any backend language with concurrency support (Go/goroutines, Python/threads, Java/ExecutorService)
- **Demo**: Submit 10 tasks, watch them get processed by 3 workers in parallel

**Level 2: Make it real** 
- Make queue persistent (survive restarts): use Redis, database, or message queue (RabbitMQ, AWS SQS)
- Implement different scheduling algorithms:
  - Priority queue (high priority tasks first)
  - Shortest Job First (if you know task duration)
  - Round Robin (for fairness)
- Add task lifecycle: pending  -> running  -> completed/failed
- Handle failures: retry logic with exponential backoff, dead letter queue (DLQ) for permanently failed tasks
- Add graceful shutdown: wait for in-progress tasks to finish
- **Demo**: Submit tasks with different priorities, show they execute in correct order, show retry logic

**Level 3: Make it yours** 

Pick ONE challenge:
- **Can you dynamically scale workers?** Add/remove workers based on queue depth
- **What if tasks timeout?** Implement task cancellation and timeout handling

**Measure what you built:**
- Throughput: tasks processed per second
- Worker utilization: percentage of time workers are busy vs idle
- Queue latency: time from task submission to task starting

---

### Data Structures & Algorithms

> **What you learned:** Arrays, linked lists, trees, graphs, sorting, searching, dynamic programming, recursion

---

#### **Path Finding Visualizer for Campus Navigation**

**Synergy / Why build this:** You learned Dijkstra's and A* in class, now implement them for real campus navigation!

**Job skills:** `graph-algorithms` `algorithm-optimization` `backend-language` `data-visualization` `api-design`  
**Coursework:** `graph-algorithms` `shortest-path` `heuristics` `data-structures`

---

**Level 1: Make it work** 
- Model your campus as a graph: buildings as nodes, paths as edges (with distances)
- Implement BFS (for unweighted) or Dijkstra's algorithm (for weighted)
- API: given start and end building, return shortest path
- Store graph data: adjacency list or edge list in your code or database
- **Tech**: Any backend language, any way to store graph data
- **Demo**: "Find shortest path from Engineering building to Library"

**Level 2: Make it real** 
- Implement multiple algorithms: BFS, Dijkstra, A* (with Euclidean distance heuristic)
- Add real constraints: closed paths, construction zones (dynamic graph updates), accessibility (wheelchair-accessible routes)
- Store graph in database with proper schema: Nodes (building_id, lat/lon), Edges (from, to, distance, type)
- Build a simple web interface to visualize paths (map library like Leaflet.js)
- Support multi-stop routing: visit multiple buildings in optimal order
- **Database**: Relational database (Postgres with PostGIS for geo data) or graph database (Neo4j)
- **Hosting**: Deploy API + frontend (Vercel/Netlify for frontend, Render/Railway for API)
- **Demo**: Interactive map where you click start/end, see path drawn

**Level 3: Make it yours** 

Pick ONE challenge:
- How much faster is A* than Dijkstra? Measure nodes explored, execution time, implement bidirectional search


**Measure what you built:**
- Algorithm execution time: milliseconds to find path (target: <100ms)
- Nodes explored: compare Dijkstra vs A* (A* should explore fewer)
- Path quality: is returned path actually optimal? Verify with manual calculation
---

### Web Development

> **What you learned:** HTML/CSS, JavaScript, DOM manipulation, responsive design, frontend frameworks, state management, RESTful APIs

---

#### **Component Library with npm Publishing**

**Synergy / Why build this:** This teaches you component architecture, API design (what props should a component accept?), accessibility (keyboard navigation, screen readers), and distribution (publishing to npm).

**Job skills:** `component-architecture` `react` `typescript` `accessibility` `npm` `testing`  
**Coursework:** `component-design` `state-management` `event-handling` `dom-manipulation`

---

**Level 1: Make it work** 
- Build 5-8 core components: Button, Input, Card, Modal, Dropdown
- Implement in React (or your preferred framework: Vue, Svelte)
- Basic styling with CSS (modules, styled-components, or Tailwind)
- Create a demo page showing all components with different variants
- **Tech**: React + CSS approach of your choice
- **Demo**: "Here are my components with different sizes, colors, states"

**Level 2: Make it real** 
- Add TypeScript for type-safe props and better DX (developer experience)
- Add Storybook for interactive documentation (each component = story)
- Write tests: Jest + React Testing Library (user interactions, edge cases)
- Support theming: light/dark mode, custom colors
- Bundle for distribution: optimize for tree-shaking (only import what you use)
- **Demo**: Live Storybook showing all components, interactive controls

**Level 3: Make it yours** 

Pick ONE challenge:
- **Can you publish to npm?** Research versioning (semantic versioning), package.json setup, how to test locally before publishing
- **How small can you make the bundle?** Measure bundle size, optimize with code splitting, lazy loading

**Measure what you built:**
- Bundle size: total KB (gzipped) for each component


---

### Cloud Computing / DevOps

> **What you learned:** Cloud platforms, virtualization, containers, orchestration, infrastructure as code, CI/CD, monitoring

---

#### **Multi-Tier Web App on AWS with Infrastructure as Code**

**Synergy / Why build this:** Coursework teaches cloud theory, this project makes you actually deploy production infrastructure. You'll learn a bunch of things from EC2, RDS, S3, Load Balancers to automating everything with code (Terraform/CDK).

**Job skills:** `aws` `infrastructure-as-code` `terraform` `cloud-architecture` `deployment` `security`  
**Coursework:** `cloud-architecture` `networking` `databases` `security` `virtualization`

---

**Level 1: Make it work** 
- Deploy a 3-tier app manually in AWS Console:
  - **Frontend**: Static files in S3 
  - **Backend**: EC2 instance running your API (from a previous project!)
  - **Database**: RDS 
- Configure security groups: only allow necessary ports (80/443 for web, 5432 for Postgres from backend only)
- **Tech**: Any frontend + backend from previous projects, AWS free tier
- **Demo**: "Here's my app running on real AWS infrastructure" with public URL

**Level 2: Make it real** 
- Add Application Load Balancer (ALB) in front of backend for better routing
- Set up Auto Scaling Group (ASG): automatically add/remove EC2 instances based on traffic
- Add CloudFront CDN for S3 static assets (faster global delivery)
- Set up CloudWatch: monitor CPU, memory, disk, set alarms for high usage
- **Automate with Infrastructure as Code**:
  - Write Terraform (or AWS CDK if you prefer TypeScript/Python) to define all infrastructure
  - Version control your infrastructure code (Git)
  - Goal: `terraform apply` creates entire infrastructure, `terraform destroy` tears it down
- **Hosting**: Production AWS account (stay in free tier or budget carefully)
- **Demo**: Show Terraform code, run `terraform apply`, show infrastructure being created

**Level 3: Make it yours** 

Pick ONE challenge:
- **How much does this cost?** Set up AWS Cost Explorer

**Questions to explore:**
- Why use a Load Balancer instead of pointing directly to EC2? (Research scaling, health checks, fault tolerance)
- What's the tradeoff between many small instances vs few large instances?

---

#### **CI/CD Pipeline with Multi-Environment Deployments**

**Synergy / Why build this:** You've built projects, now automate testing and deployment. This teaches you the full software delivery lifecycle: code  -> test  -> build  -> deploy, exactly what companies do daily.

**Job skills:** `ci-cd` `github-actions` `docker` `automated-testing` `deployment` `devops`  
**Coursework:** `software-engineering` `testing` `automation` `deployment`

---

**Level 1: Make it work** 
- Set up GitHub Actions workflow for one of your previous projects
- On every push: run linter (ESLint, pylint, gofmt)  -> run tests
- If tests pass: build Docker image  -> push to Docker Hub or GitHub Container Registry
- **Tech**: GitHub Actions (free for public repos), Docker
- **Demo**: Push code, watch GitHub Actions run, see green checkmark (or red X if tests fail)

**Level 2: Make it real** 
- Create multiple environments: **dev**, **staging**, **production**
- Run different jobs for different branches:
  - Any push  -> lint + test
  - Push to `develop`  -> deploy to dev environment
  - Push to `main`  -> deploy to staging, then production (after approval)
- Add integration tests that run against real services (use Docker Compose in CI)
- Run security scans: Trivy for container images, Snyk for dependencies
- Add Discord notifications on build success/failure
- **Demo**: Push to dev branch  -> auto-deploy to dev URL, push to main  -> auto-deploy to production URL

**Level 3: Make it yours** 

Pick ONE challenge:
- **Can you implement automated rollback?** If post-deployment smoke tests fail, automatically revert to previous version
- **How would you speed up CI?** Research: caching dependencies, parallel jobs, incremental builds
- **Can you add performance regression testing?** Fail the build if API response time increases by >10%


**Measure what you built:**
- Pipeline duration: time from push to deployed (aim for <5 minutes for simple apps)
- Test coverage: percentage of code covered by automated tests (aim for >80%)
---

### Distributed Systems

> **What you learned:** Consensus, replication, CAP theorem, fault tolerance, distributed algorithms, consistency models

---

#### **Event-Driven Microservices with Message Queue**

**Synergy / Why build this:** Monolithic apps become unmanageable at huge scale. Companies split into microservices that communicate asynchronously. This teaches you event-driven architecture (services publish events, others subscribe), message queues (reliable async communication), and distributed system patterns.

**Job skills:** `microservices` `event-driven-architecture` `message-queues` `distributed-systems` `backend-language`  
**Coursework:** `distributed-systems` `asynchronous-processing` `messaging` `fault-tolerance`

---

**Level 1: Make it work** 
- Build 3 simple services that communicate via messages:
  - **Order Service**: receives orders, publishes "OrderCreated" event
  - **Inventory Service**: subscribes to orders, decrements stock
  - **Notification Service**: subscribes to orders, sends confirmation (log to console)
- Use a message queue: RabbitMQ, Redis Pub/Sub, or cloud service (AWS SQS)
- Each service is independent: own code, own database (or own table)
- **Tech**: Your favorite backend language, RabbitMQ (Docker) or Redis
- **Demo**: Submit order  -> watch messages flow between services  -> see stock decrease and notification sent

**Level 2: Make it real**
- Make queues persistent: messages survive broker restarts
- Add proper error handling:
  - Retry logic: if processing fails, retry with exponential backoff
  - Dead Letter Queue (DLQ): after max retries, move to DLQ for manual inspection
- Implement idempotency: processing the same message twice should be safe
  - Track processed message IDs in database
- Add monitoring: message queue depth, processing rate, error rate
- Give each service its own database (true microservices) and handle transaction boundaries
- Deploy services independently: each service has its own Docker container
- **Message Queue**: RabbitMQ with persistence, or managed service (AWS SQS, CloudAMQP)
- **Hosting**: Deploy all services (Docker Compose locally or cloud platform)
- **Demo**: Kill a service mid-processing  -> show messages are retried  -> show DLQ for permanently failed messages

**Level 3: Make it yours** 

Pick ONE challenge:
- **How would you guarantee message order?** Some systems need strict ordering
- **Can you handle eventual consistency?** What if Inventory Service is down? 
- **How would you add observability?** Trace a single order through all services (research distributed tracing with Jaeger or Zipkin)


**Measure what you built:**
- End-to-end latency: time from order created  -> all services processed
- Service independence: can you deploy one service without affecting others?
- **Tools**: Message queue monitoring (RabbitMQ UI, CloudWatch for SQS), timing logs across services, load testing

---

## Contributing

This guide is a living document. Contributions welcome:

- ✅ Implementation examples (link your GitHub repo)
- ✅ Improvements to existing project descriptions
- ✅ Better "questions to explore" or measurement strategies


---

## Let's Connect

Building in public. Sharing what works.

**Find me:**
- **GitHub**: https://github.com/owenHochwald/
- **LinkedIn**: https://www.linkedin.com/in/ohoch/

---

## If This Helped You

- **Star this repo** ⭐
- **Build** one of these projects
- **Share** your implementation with others
- **Document your metrics** and lessons learned

---